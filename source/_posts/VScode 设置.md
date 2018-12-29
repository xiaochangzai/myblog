---
title: VScode 设置
---

```
{
    "terminal.integrated.shell.windows": "C:\\Windows\\System32\\cmd.exe",
    "files.autoSave": "onWindowChange",
    "workbench.iconTheme": "material-icon-theme",
    "editor.tabSize": 4,
    "emmet.triggerExpansionOnTab": true,
    "emmet.showExpandedAbbreviation": "inMarkupAndStylesheetFilesOnly",
    "emmet.includeLanguages": {
    "vue-html": "html",
    "vue": "html",
    "wxml": "html"
    },
    "emmet.syntaxProfiles": {
    "javascript": "jsx",
    "vue": "html",
    "vue-html": "html"
    },
    "files.associations": {
    "*.wxml": "wxml",
    "*.wxss": "css",
    "*.wxs": "javascript",
    "*.wpy": "html",
    "*.vue": "vue"
    },
    "minapp-vscode.disableAutoConfig": true,
    "minapp-vscode.wxmlQuoteStyle": "'",
    "emmet.optimizeStylesheetParsing": false,
    "eslint.autoFixOnSave": true,
    "eslint.options": {
    "extensions": [
    ".js",
    ".vue"
    ]
    },
    "eslint.validate": [
    "javascript",{
    "language": "vue",
    "autoFix": true
    },"html","vue"
    ],
    "search.exclude": {
    "**/node_modules": true,
    "**/bower_components": true,
    "**/dist": true
    },
    "window.zoomLevel": 0
}


```