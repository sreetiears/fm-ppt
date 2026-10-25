# 如何看论文 · 新生研讨课

开放原子开源社团 45 分钟研讨课。先撰稿，再做精简幻灯片。主例子是 MinerU。

## 独立环境

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

激活：

```powershell
.\.venv\Scripts\Activate.ps1
```

## 文档

- [调研笔记](docs/research-notes.md)：高星参考、Keshav 三遍法、Claude 设计决策
- [宣讲稿](docs/speaker-script.md)：45 分钟逐字稿和舞台提示
- [PPT 大纲](docs/slide-outline.md)：锁定后的 19 页结构

## 交付

- `slides/how-to-read-papers.html`：课堂主演示（16:9 单文件）
- `slides/how-to-read-papers.pptx`：教室备份

## 参考

内容：S. Keshav, *How to Read a Paper* (2007)；MinerU, arXiv:2409.18839。  
制作：frontend-slides、awesome-design-md（Claude）、ppt-master（仅流程参考）。
