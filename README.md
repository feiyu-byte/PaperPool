# PaperPool

本项目的目录结构：

```bash
paperpool/
├── assert_db
│   └── ...
├── paper_list.txt
├── README.md
└── review_db
    └── ...
```

在 `paper_list.txt` 中记录了被筛选出打算或已经阅读的论文条目。条目的格式参考
[该语雀文档](https://serve.yuque.com/mora7e/is769v/ktw12d2c5s9c04mf)，并在条目
的头部添加 `% REVIEWED: FALSE` 或 `% REVIEWED: TRUE` 标记该篇论文是否被阅读过。
条目之间使用一个空行进行分隔。条目均使用“期刊时间-内容摘要”的形式进行唯一命名。
下面是一个条目的例子：

``` bibtex
% REVIEWED: FALSE
@inproceedings{FPL22-Cloud-FPGA,
  author    = {Ruan, Jinjie and Chang, Yisong and Zhang, Ke and Shi, Kan and Chen, Mingyu and Bao, Yungang},
  title     = {Increasing Flexibility of Cloud FPGA Virtualization},
  booktitle = {2022 32nd International Conference on Field-Programmable Logic and Applications (FPL)},
  pages     = {350--357},
  year      = {2022},
}
```

在 `review_db` 中记录了对 `paper_list.txt` 中论文的阅读记录。每一个文件对应一条
阅读记录。文件的命名与上述唯一命名一直，例如：`FPL22-Cloud-FPGA.md`。每一条阅读
记录的具体格式如下：

``` markdown
# 论文标题

中文简述标题

链接到出版商网站的 URL

## 研究背景和意义

...

## 相关工作及评价

...

## 主要方法与创新点

...

## 实验设置和结论

...

## 创新、不足和相关性评论

...

## 对 REVIEW 的评论

贵缘（2024.9.3）：...

飞羽（2024.9.3）：...

...
```

文档中的所有图片均放在 `assert_db` 文件下，并在 `paper_db` 中使用 markdown 语法
相对链接到图片资源，如 `FPL22-Cloud-FPGA 的主要结构为 ![](assert_db/....jpg)`。
