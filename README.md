
# PlatterzStackEdit

Hi Guys, 

Sorry, I could not be on this long, still have some arrangements I need to do before starting to work full time.
Here is what I did so far:

(Warning, super ugly code)

1. Changing the MD file is not an issue, it simply loads only once the “welcome file”.

2. For checking left side validation, I found “checkContentChange” function at “cleditCore.js” file to be called on every change. And adding a functino call “checkForErrors()”, app will look for ranges on character “-“ and keep it at: ErrorIndexSvc.getInstance().errorsIndexes = indexes;

3. Displaying an error button on the left, at the error position, I have hacked “EditorNewDiscussionButton,” by creating equal number of div’s equal to the number of indexes with errors, and displaying an error button on the left.

4. Pressing the button will call the old “discussion” logic, I think the best option would be to open a pop up, there is a pop up that shows when user first enters the app: 
``<tour v-if="!light && !layoutSettings.welcomeTourFinished"></tour>``
It would probably be a good option to use it.

To see the error buttons, simply run application. And whenever entering the charicate "-", a red alert button would apear of the left.

Sorry, could not help more, see you soon.

# StackEdit

[![Build Status](https://img.shields.io/travis/benweet/stackedit.svg?style=flat)](https://travis-ci.org/benweet/stackedit) [![NPM version](https://img.shields.io/npm/v/stackedit.svg?style=flat)](https://www.npmjs.org/package/stackedit)

> Full-featured, open-source Markdown editor based on PageDown, the Markdown library used by Stack Overflow and the other Stack Exchange sites.

https://stackedit.io/

### Ecosystem

- [Chrome app](https://chrome.google.com/webstore/detail/iiooodelglhkcpgbajoejffhijaclcdg)
- NEW! Embed StackEdit in any website with [stackedit.js](https://github.com/benweet/stackedit.js)
- NEW! [Chrome extension](https://chrome.google.com/webstore/detail/ajehldoplanpchfokmeempkekhnhmoha) that uses stackedit.js
- [Community](https://community.stackedit.io/)

### Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm start

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

### StackEdit can:

 - Manage multiple Markdown files online or offline
 - Export your files in Markdown, HTML, PDF, Word, EPUB...
 - Synchronize your Markdown files in the Cloud
 - Edit existing Markdown files from Google Drive, Dropbox and your local hard drive
 - Post your Markdown file on Blogger/Blogspot, WordPress, Zendesk
 - Publish your Markdown file on GitHub, Gist, Google Drive, Dropbox
 - Share a workspace over Google Drive, CouchDB

### Features:

 - Real-time HTML preview with Scroll Sync feature to bind editor and preview scrollbars
 - Markdown Extra/GitHub Flavored Markdown support and Prism.js syntax highlighting
 - LaTeX mathematical expressions using KaTeX
 - Diagrams and flowcharts using Mermaid
 - WYSIWYG control buttons
 - Smart layout
 - Offline editing
 - Online synchronization using Google Drive, Dropbox and GitHub
 - One click publish to Blogger, Dropbox, Gist, GitHub, Google Drive, WordPress, Zendesk

> **NOTE:** This page has been written and published with [StackEdit](https://stackedit.io/ "StackEdit").
