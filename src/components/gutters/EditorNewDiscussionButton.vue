<template>

<div>
        <template v-for="(item) in indexesCoordinates">
          <a :key="item" class="new-discussion-button" href="javascript:void(0)" v-if="item" :style="{top: item + 'px'}" v-title="'Start a discussion'" @mousedown.stop.prevent @click="createNewDiscussion(selection)">
    <icon-alert></icon-alert>
  </a>
        </template>
    </div>
</template>

<script>
import { mapActions } from 'vuex';
import editorSvc from '../../services/editorSvc';
import store from '../../store';
import ErrorIndexSvc from '../../services/ErrorIndexesSvc.ts';

export default {
  data: () => ({
    selection: null,
    coordinates: null,
    indexesCoordinates: null,
  }),
  methods: {
    ...mapActions('discussion', [
      'createNewDiscussion',
    ]),
    checkSelection() {
      console.log('checkSelection');
      clearTimeout(this.timeout);
      this.timeout = setTimeout(() => {
        let offset;
        // Show the button if content is not a revision and has the focus
        if (
          !store.state.content.revisionContent &&
          editorSvc.clEditor.selectionMgr.hasFocus()
        ) {
          this.selection = editorSvc.getTrimmedSelection();
          if (this.selection) {
            const text = editorSvc.clEditor.getContent();
            offset = this.selection.end;
            while (offset && text[offset - 1] === '\n') {
              offset -= 1;
            }
          }
        }
        const nextIndexesCoordinates = [];
        for (let i = 0; i < ErrorIndexSvc.getInstance().errorsIndexes.length; i += 1) {
          const errorIndex = ErrorIndexSvc.getInstance().errorsIndexes[i];
          const current = editorSvc.clEditor.selectionMgr.getCoordinates(errorIndex).top;
          if (!nextIndexesCoordinates.includes(current)) {
            nextIndexesCoordinates[i] = current;
          }
        }
        this.indexesCoordinates = nextIndexesCoordinates;
        this.coordinates = offset
          ? editorSvc.clEditor.selectionMgr.getCoordinates(offset)
          : null;
      }, 25);
    },
  },
  mounted() {
    this.$nextTick(() => {
      editorSvc.clEditor.selectionMgr.on('selectionChanged', () => this.checkSelection());
      editorSvc.clEditor.selectionMgr.on('cursorCoordinatesChanged', () => this.checkSelection());
      editorSvc.clEditor.on('focus', () => this.checkSelection());
      editorSvc.clEditor.on('blur', () => this.checkSelection());
      this.checkSelection();
    });
  },
};
</script>
