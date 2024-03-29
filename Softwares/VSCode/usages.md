# VS Code 常見配置與使用情境

## 常用快捷鍵 - 編輯

⇧⌘K:刪除整列
⌥⌘↑/⌥⌘↑↓: 在當前游標位置往上/往下增加游標
⇧⌘L:在全文中尋找當前選取的文字，並全部選取
⌘D:選取下一個符合當前選取文字的文字

## 自訂視窗標題

```txt
${activeEditorShort}: the file name (e.g. myFile.txt).
${activeEditorMedium}: the path of the file relative to the workspace folder (e.g. myFolder/myFileFolder/myFile.txt).
${activeEditorLong}: the full path of the file (e.g. /Users/Development/myFolder/myFileFolder/myFile.txt).
${rootName}: name of the opened workspace or folder (e.g. myFolder or myWorkspace).
${rootPath}: file path of the opened workspace or folder (e.g. /Users/Development/myWorkspace).
${separator}: a conditional separator (" - ") that only shows when surrounded by variables with values or static text.
```

```json
// Softwares/VSCode/perference.md - ~/project/programming-note
// default: "${dirty}${activeEditorShort}${separator}${rootName}${separator}${appName}"
"window.title": "${activeEditorMedium}${separator}${rootPath}"
```

## 搜尋換列符號

```regex
<!-- 所有換列符號 -->
[\n], \n
<!-- 空白列 -->
^$\n
```

## Markdown 快捷指令

需要先安裝 `yzhang.markdown-all-in-one` 套件

- 提高標題層級：⇧⌃[
- 降低標題層級：⇧⌃]
- 添加列表項目符號和更新列表項目符號：⇧⌘P (show all commands)，執行 `Markdown All in One: Toggle list`

> 設定可使用的項目符號

```json
"markdown.extension.list.toggle.candidate-markers": [
    "-",
    "1."
],
```
