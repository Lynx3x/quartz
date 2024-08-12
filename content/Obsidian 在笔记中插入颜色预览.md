---
date: 2024-07-28 23:38:43
tags:
  - 来源/个人
  - 工具/Obsidian
  - 领域/设计/色彩
source:
---
- 发了个视频之后，评论区底下有好心人，给我推荐了 [obsidian-css-inlay-colors](https://github.com/GRA0007/obsidian-css-inlay-colors) 插件，只要使用行内代码块的语法输入色号，就会自动在前面显示颜色对应的色块了
	- 有个 bug ，在列表下无法正常显示，提了个 Issue，作者飞快修好了，太好用了


## 前言

想要在一些 UI 设计笔记里面更直观地标识颜色，记得一些 APP 里面有颜色预览功能，想试着找找有没有办法

## 效果

<span style="color: #ff00ff ">■</span><kbd><span>#</span>ff00ff</kbd>

## 步骤

使用 HTML 语法，把实心方块的颜色改变，然后再在后面标注上色号

### 实心方块

```
<span style="color: #ff00ff">■</span>
```

### 色号

```
<kbd><span>#</span>ff00ff</kbd>
```

原教程中使用的是 `<kdb>` 标签，显示效果跟单行语法块是一样的，直接简单使用单行语法块的语法处理了

## 优化：使用模板快捷输入

- 使用 Templater 插件（至少 1.0.0版本）
	- 较为轻量级，并且使用广泛的插件，没有心智负担

创建一个 ColorTemplate 模板文件

```
<span style="color:   <% tp.file.selection() %>  ">■</span> `# <% tp.file.selection() %> `
```

在使用时，需要先把 RGB 色号写出来（例如 7C3AED），然后将其选中后，再调用模板

<span style="color: 7C3AED">■</span> `#7C3AED`

也可以自行修改模板，将方块改为其他（例如圆形）、将方块之后，或者用什么东西包起来之类的
## 参考

- [Render preview of a color in a file - Feature requests - Obsidian Forum](https://forum.obsidian.md/t/render-preview-of-a-color-in-a-file/47042/3)
	- 主要参考
- [can a template action be based on the "current selection" in the editor? · Issue #44 · SilentVoid13/Templater](https://github.com/SilentVoid13/Templater/issues/44)
	- 模板语法，返回选中当前内容
	- [tp.file - Templater](https://silentvoid13.github.io/Templater/internal-functions/internal-modules/file-module.html?highlight=selection#tpfileselection)
