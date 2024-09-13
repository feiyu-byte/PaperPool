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
条目均使用“期刊时间-内容摘要”的形式进行唯一命名。下面是一个条目的例子：

``` bibtex
% REVIEWED: FALSE
@inproceedings{FPL22-Cloud-FPGA,
  author={Ruan, Jinjie and Chang, Yisong and Zhang, Ke and Shi, Kan and Chen, Mingyu and Bao, Yungang},
  title={Increasing Flexibility of Cloud FPGA Virtualization},
  booktitle={2022 32nd International Conference on Field-Programmable Logic and Applications (FPL)},
  pages={350--357},
  year={2022},
}
```

在 `review_db` 中记录了对 `paper_list.txt` 中论文的阅读记录。每一个文件对应一条
阅读记录。文件的命名与上述唯一命名对应，例如：`FPL22-Cloud-FPGA.md`。每一条阅读
记录的具体格式如下：

``` markdown
# 论文标题

中文简述标题

链接到出版商网站的 URL

## 研究问题和意义

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

下面是对上述模板的详细解释：
1. 研究问题和意义：在这一段落应该说明该文章要解决的核心问题，和解决了该问题可以
   带来哪些现实效益。这些信息一般出现在 Abstract 的前两句话，和 Introduction 的
   前三段。
2. 相关工作及评价：在这一段落应该记录站在该文章作者的视角，哪些是相关的 SOTA 工
   作，以及该文章作者对这些相关工作的评价。在 Abstract 的第三句话或者第四句话一
   般会存在对相关工作的泛泛评论。在 Introduction 部分的中间部分会有一组引用和对
   这些引用的评论。大多数论文也会有专门的 Preliminaries 或 Related Work 节，有的
   在 Introduction 后面，也有的在 Conclusion 前面。在整理这一段内容的过程中，注
   意以梳理研究脉络为主，关注重要的 SOTA 工作，忽略掉 Introduction 最前面只是用
   来写作的引用文献。编写这一段的时候可以使用如下句式：“作者评价参考文献【30】没
   有做数据包的重排，而这对性能的影响至关重要”，或“文章评价 FPL22-Cloud-FPGA 的
   工作提供了一种 FPGA 虚拟化的思路”（对于没有收录到论文池的文献，可以使用文章中
   的编号；对于已经收录的文献，优先使用唯一编号）。 在阅读的过程中，如果发现对相
   关工作很感兴趣，请检查在论文池中是否存在。如果不存在，可以自行添加。
3. 主要方法与创新点：这一段落应该描述该文章作者宣称他们自己的方法相比于 SOTA 工
   作的创新点，也就是他们的具体设计。这一段落对应文章从相关工作到结论中间的所有
   主体部分，越前面越总览，越后面越精细。有的文章有 Overview 小节来说明整个工作
   的结构。在整理这一段的时候注意精简描述，不要大段摘抄或者翻译原文。
4. 实验设置和结论：在这一段记录文章做了哪些实验和主要的测试指标结果即可。只需要
   给数据，不需要太多。
5. 创新、不足和相关性评论：这一段落用于编写该论文与其他工作的关系，我们对该论文
   创新、不足的评论（注意，和前一部分论文作者宣称的创新点相区分），以及该文章和
   我们工作的关系（我们的工具能否支持他们的工作？他们的工作能否帮助我们的工具演
   进？）
6. 对 REVIEW 的评论：这一段落在第一个人粗度并编写文档的时候留空，只写出标题。其
   他人可以在这个区域对论文和 REVIEW 本身做出评论。

上述记录注意精简，三百到五百字为宜。目的在于保证自己阅读速度的同时，也能让其他人
快速了解这篇工作的内容。如果有暂时没读懂的地方，给出原文中的段落位置即可。

文档中的所有图片均放在 `assert_db` 文件下，并在 `paper_db` 中使用 markdown 语法
相对链接到图片资源，如 `FPL22-Cloud-FPGA 的主要结构为 ![](assert_db/....jpg)`。
