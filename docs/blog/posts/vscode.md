---
title: VSCode settings I'm accustomed to 
date: 
  created: 2025-05-22
authors: [Pengyu-Jin]
slug: vscode seetings
categories:
  - Research
---

Vim enthusiasts are always looking for convenience, and I'm no exception.

<!-- more -->

| shortcut key | function |
| ----------- | --------- |
| ++ctrl+tilde++ | toggle terminal |
| ++ctrl+shift+tilde++ | create new terminal |
| ++ctrl+slash++| 选中批量注释or取消注释 toggle line comment  |
| ++shift+tab++ | 批量取消tab缩进  |
| ++ctrl+shift+n++ | create new window|
| ++alt+b++   | open/close the sidebar|
| ++ctrl+h++  | move the cursor to explorer in the vim `normal mode`|
| ++ctrl+l++  | reverse operation|
| ++ctrl+tab++ | switch tabs |



## some notes
open the `Keyboard Shortcuts`

search `selectPrevSuggestion`, set it to ++ctrl+k++

search `selectNextSuggestion`, set it to ++ctrl+j++

## Vim Tips

you can use the use the folling sequence to *delete around* a pair of quotes (included), which are the cloest pair of quotes to your cursor:
```
da"
```
*delete inside* sequence to delete the characters whinin the quotes whinout deleting the quotes:
```
di"
```
*change inside* sequence to reomve the characters and switch to insert mode
```
ci"
```