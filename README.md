# 反向排序工具（含 OCR）

两个功能凑在一个页面上：**把一批文本行倒过来排**，以及**从图片里把文字抠出来**（截图、照片都行，中文英文都认）。

[打开工具 →](https://abububu903.github.io/reverse-sort-tool/) · [English](#english)

---

## 打开就用

👉 **[abububu903.github.io/reverse-sort-tool](https://abububu903.github.io/reverse-sort-tool/)**

不用安装、不用注册。想本地跑：下载 `index.html` 双击打开即可。

> 唯一需要联网的地方：OCR 的识别模型（tesseract.js）第一次点「图片 OCR」时才从 CDN 下载。纯文本反向排序完全离线可用。

## 反向排序：一个例子

**注意：这里是把「行的顺序」颠倒，不是把文字按字母倒排。**

输入（每行一条）：

```
苹果
香蕉
橙子
```

点「反向排序」，输出：

```
橙子
香蕉
苹果
```

典型用法：一列数据倒过来看、把从屏幕下方往上截取的行恢复成正常阅读顺序、名单首尾调换。

## 图片 OCR：怎么用

1. 点「图片 OCR」，或直接把截图 **粘贴（⌘V / Ctrl+V）** 到页面里
2. 用鼠标**拖动框选**要识别的那块区域，松开即开始识别（按 `Esc` 或「取消」可放弃）
3. 识别出的文字进入输入框，可以接着点「反向排序」

适合的场景：手里只有一张表格截图、PDF 转出来的图片、聊天里收到的文字截图，不想手抄。

## 关于识别准确率

OCR 是图像识别，不是魔法，以下几类容易出错：

- 手写体、艺术字、低分辨率小字
- 拍歪了、有反光、阴影的照片
- 密集表格里的数字，可能串行

**识别完请自己核对一遍关键内容**（尤其是数字和金额）。

## 隐私

图片在浏览器本地识别，不会上传到任何服务器；页面不存任何东西，刷新即清空。

## 文件说明

| 文件 | 作用 |
| --- | --- |
| `index.html` | 工具本体，页面 + 样式 + 排序与 OCR 逻辑全在这一个文件里 |
| `README.md` | 你正在看的这个说明页，GitHub 自动展示在仓库首页 |

## 已知边界

- 一行算一条，不做去重、不做排序规则自定义（只颠倒，不字典序排）
- OCR 语言包固定 `chi_sim+eng`（简中 + 英文），繁体、日文等不在范围内
- 「复制结果」依赖浏览器剪贴板权限，个别浏览器需手动选中复制

---

## English

A single-page utility that does two things: **reverse the order of text lines**, and **pull text out of an image** (screenshots or photos, Simplified Chinese + English).

- **Live page:** <https://abububu903.github.io/reverse-sort-tool/> — no install, no sign-up. Or download `index.html` and open it directly.
- **Reverse ≠ sort descending.** The button flips the line order top-to-bottom (`lines.reverse()`); it does not alphabetize anything.
- **OCR:** click "图片 OCR" or paste a screenshot, then drag a rectangle over the region you want. Recognition runs locally in your browser via tesseract.js — the image never leaves your machine. The model itself downloads from a CDN on first use, so OCR needs network once; plain reversing works fully offline.
- **Accuracy:** handwriting, skewed or glare-affected photos and dense tables can misread. Proofread anything that matters.
- **Scope:** one line per entry, no dedupe or custom sort keys; language pack is fixed to `chi_sim+eng`.

*By abububu903.*
