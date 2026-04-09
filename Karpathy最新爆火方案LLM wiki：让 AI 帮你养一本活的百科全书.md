# Karpathy最新爆火方案LLM wiki：让 AI 帮你养一本活的百科全书
🔥 AI 知识管理

上周，Andrej Karpathy（前特斯拉 AI 总监、OpenAI 联合创始人）在 GitHub 上发了一篇短文，两天内收获 **1400+ Star**，全网刷屏。

他说了一件很简单的事：

我现在花在"用 AI 管理知识"上的 token，比"用 AI 写代码"还多。

—— Andrej Karpathy

翻译成大白话就是：**他不再只是让 AI 帮他写程序了，而是让 AI 帮他读文章、做笔记、整理知识、查漏补缺。** 

更重要的是，他分享了具体怎么做。

我读完之后马上用小龙虾+Obsidian照做了一套，用来管理自己"学 AI"的所有资料——论文、教程、视频笔记、想法碎片。感觉效果不错，想写出来分享给大家。

· · ·

Part 1

先搞懂：Karpathy 到底在说什么？
--------------------

你平时是怎么"学东西"的？大概是这样：

看到一篇好文章 → 收藏 → 再也不打开。  
看了个好视频 → 觉得"学到了" → 三天后忘干净。  
存了一堆 PDF → 躺在文件夹里落灰。

就算你用了笔记软件，结果通常也是：**前两周很勤快，第三周开始偷懒，第四周彻底放弃。** 

为什么？因为整理笔记太累了——写摘要、打标签、做链接、保持更新……这些"维护工作"的负担增长得比知识本身还快。

💡 Karpathy 的核心洞察

人类放弃知识库，不是因为懒，而是因为维护的成本太高了。但 AI 不会累、不会忘，一次能同时更新十几篇笔记。**让 AI 来做所有的"苦力活"，你只管收集资料和思考。** 

### 传统方式 vs Karpathy 方式

| 

传统方式（RAG）

 | 

Karpathy 方式（LLM Wiki）

 |
| --- | --- |
| 

每次提问，AI 临时从文件里翻找答案

 | 

AI 提前把所有资料消化好、整理成百科

 |
| 

问完就忘，知识不积累

 | 

每次提问的好回答都存回知识库

 |
| 

文档之间没有关联

 | 

所有概念互相链接，形成知识网

 |
| 

你自己做整理员

 | 

AI 做整理员，你做馆长

 |

### 知识库系统长什么样？就三层

![](https://mmbiz.qpic.cn/mmbiz_png/n14MNgLbALkszASum4MqVteiaC0xgXOI0Z0OjantHUTY71EiaodsJlOwzmHbFFZmdZnWkoPzAmGy0J573woCnffucBibDAibhVxvOJ5APF1EhGY/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=0)

而AI 在这套系统里做**三件事**：

![](https://mmbiz.qpic.cn/sz_mmbiz_png/n14MNgLbALlLPwSv953ZwmRdTiavE7WzvNhTgVFmpNyk9mmanWnKCQjo9msFfrnBdJDR5daKGwNN5FvpNV84ZQobC3OIwG43ica7cXyX8ibUdg/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=1)

· · ·

Part 2

为什么我选小龙虾OpenClaw + Obsidian？
----------------------------

Karpathy 原文提到用LLM+Obsidian来实现。而最近可谓人人都有几只小龙虾，让小龙虾和Obsidian配合，极大方便了我们对知识库的整理。

**Obsidian** 是一个免费笔记软件，笔记存在你自己电脑上，笔记之间可以互相链接，还有很酷的"图谱视图"。它是知识库的**展示前端**。

**OpenClaw** 大家都知道了，是一个开源的 AI 助手，跑在你自己的电脑上或者云端。它最大的特点是：你可以**在微信、飞书、Telegram 等聊天软件里跟它对话**，而且它可以 24 小时在线、自动执行任务。它是知识库的**后台引擎**。

我的实践：搭建一个「学 AI」知识库
------------------

我用这套方案来管理自己学 AI 的所有资料——论文、教程、课程笔记、大佬分享、自己的想法。下面是完整过程。

### 第一步：搭建基础设施

#### 01 安装 Obsidian

去 obsidian.md 下载安装，创建一个新仓库叫 `AI 学习库`。然后建好文件夹结构：

AI 学习库/  
 ├── raw/ ← 原始资料（你收集的）  
 │ └── assets/ ← 存放图片  
 ├── wiki/ ← AI 维护的知识百科  
 └── output/ ← 生成的报告、图表

#### 02 安装 OpenClaw 并连接聊天软件

这个就不多说了，大家随便网上搜搜就能够找到，也可以使用各大厂的一键安装。

#### 03 创建知识库管理 Skill

这是关键一步——写一份"工作说明书"告诉 AI 该怎么整理笔记。在 `.openclaw/skills/kb-manager/SKILL.md` 里写入规则：摄入时做什么、查询时怎么回答、体检时检查什么。（详细内容关注公众号，留言“AI知识库管理”获得）

### 第二步：开始喂资料

基础设施搭好了，接下来就是**最爽的部分**——往里丢东西，看着知识库自动生长。

📝 场景 1：看完一篇文章

我看了 Lilian Weng 的《Attention Is All You Need 论文解读》。用 Obsidian Web Clipper（这是一个浏览器插件，可以把web的文章转换成markdown格式），一键保存到 `raw/` 文件夹，然后在 Telegram 里跟 OpenClaw 说一声：

![](https://mmbiz.qpic.cn/mmbiz_png/n14MNgLbALliaibBG4Fo7IZM5WgvLicGYtw94hrzA3dDekUpKpXpTDDvIMu1PJficmjalFVeuFJbPxrnPG0E19J9xJ82gvOic05H0dxZEmBpwXYs/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=2)

打开 Obsidian 一看，wiki 文件夹里已经有了 6 个互相链接的页面。点开图谱视图，一张小小的知识网开始形成了。

![](https://mmbiz.qpic.cn/mmbiz_png/n14MNgLbALlzhJYIKXt7yJmGKOPibe61q6yycHSzxLX9LMgicpJtorWxMLLibHtQ7XMVFqow2QP75Aeiaibjqvb2eP9aYSF85jRCArwgsHvgCp9I/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=3)

                                 🕸️ Obsidian 图谱视图  
  

📝 场景 2：在地铁上听完播客

听了一期 Lex Fridman 采访 Ilya Sutskever 的播客，里面有个观点很有意思——"数据可能比模型大小更重要"。掏出手机：

![](https://mmbiz.qpic.cn/mmbiz_png/n14MNgLbALk27Nsktaiaup8zdkXWHduz7IMAX2QJ05DnuSibmicOMo9IId6ERMkSLrJtV6Jlic8ZdqEJ2jXxvVRaicpJfFaz7aICev0hWpMiaoTh8/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=4)

注意看——**AI 自动发现了矛盾**。这就是 Karpathy 说的"lint"功能。之前笔记里写的"更大总是更好"和新信息"数据质量可能更重要"存在张力，AI 主动帮你标出来了。

📝 场景 3：学完一门课程的一章

跟着 Andrej Karpathy 的 "Neural Networks: Zero to Hero" 学完了反向传播那一章。把课程笔记存到 `raw/` 后：

![](https://mmbiz.qpic.cn/sz_mmbiz_png/n14MNgLbALm9xRGk58GXbq0wBuR1lKTc2JyV9Nu1OEFFndFsFomnDCj4bQtmYAPHJatXd6GMyzLqElj2cbaFKy3vficBp8IuqaibNTQFTWufU/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=5)

AI 不只是被动地存笔记，它在**主动帮你思考知识的结构**——发现"训练"是一个反复出现的主题，建议把它们串成一条线。

### 第三步：设置自动化

最开始我每次都手动说"处理一下"，后来觉得这一步也可以省掉：

![](https://mmbiz.qpic.cn/mmbiz_png/n14MNgLbALmVJUt0a1QLGZEWbMBJjKdY653holZZTNOr6k2XW9zPQEyrgtFTtau9y5pFS3Jm8HtbP59EtKJG9ibibdyib7lszXqt6voT9nya0M/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=6)

从此，我的日常变成了：

![](https://mmbiz.qpic.cn/mmbiz_png/n14MNgLbALnNk4ibG4icAdT9y7eRRA5WzPXEN1p1IYdLvztBqZo85MwMShLuAke6Jv2Y3eTYFR4xDzE76XWs8AzotTYUrAnAgXCaoRqlRvREg/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=7)

### 第四步：向知识库提问

很快，我的AI知识库已经有了 30 多篇 wiki 页面。这时候提问的体验开始变得很不一样：

![](https://mmbiz.qpic.cn/mmbiz_png/n14MNgLbALkTUqJkoB8rx47EF4RmXoW4D09suImjmdTXfO4rEbKA28AWlE71mSQR7NGVicHK2GiawBic6nwCib0FKUJ4BabCMt2X6Itibyy9Cs8U/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=8)

注意两个细节：

1 AI 的回答是基于**你自己精心收集的 30 多篇资料**综合出来的，不是随便从互联网上搜的。质量远超普通 ChatGPT 对话。可以媲美NotebookLM了。

2 AI 主动发现了**知识盲区**——BERT 的资料不够。这就是 Karpathy 说的"lint"——AI 不只回答问题，还帮你发现应该去学什么。

### 第五步：进行体检

你可以定时每周日早上 9 点，对知识库进行体检，让它给你发个周报：

![](https://mmbiz.qpic.cn/sz_mmbiz_png/n14MNgLbALn7ZVUKlpYyJPaN3lXyiaWlHIXqu3ibI8VpLI0avLqEmOibYdGBDkiaG8Qicf2Ss4J6IUc4icI1lRO5abpQ5IW1bp4PqmMDexfYQHP5U/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=9)

这就像有一个 AI 学习教练，每周告诉你：你的知识图谱哪里厚、哪里薄、下一步该补什么。最后，你的知识图谱可能是这样的：

![](https://mmbiz.qpic.cn/mmbiz_png/n14MNgLbALmxA9VvBT9XGqG0cS9whMX75POTfbgbjibR2qGKNtoJbltcq2fMibRQgF2R7IRnLXBPIcdEt5TicvEbZMALrogW1MbdibBkslckZzw/640?wx_fmt=png&from=appmsg&watermark=1#imgIndex=10)

最让人惊喜的是：**在这个过程中几乎没有"整理笔记"的负担。**  你要做的事情只有三件：

1 看到好内容 → 保存到 raw/（10 秒）

2 偶尔在手机上提个问题（30 秒）

3 在 Obsidian 里浏览新增内容（享受的时间）

所有摘要、分类、链接、矛盾检测、知识盲区发现——**全部是 AI 自动完成的。** 

· · ·

Part 3

你也可以这样做，一起来尝试
-------------

这套方法适用于任何你想持续深入的领域：

📈 投资理财🏋️ 健身营养📚 考研备考🎨 设计灵感🏠 装修知识👶 育儿经验📖 读书笔记🧠 心理学

建议：

✅ 从小开始

先选一个小话题，收集 10 篇资料试试手。不要一上来就想建"人类知识总库"。

✅ 坚持投喂

前期可能觉得没什么用，坚持到 30 篇会有质变——AI 开始能回答越来越深的问题。

✅ 多提问

不要只往里塞资料。经常提问，让好的回答存回 Wiki。你的探索本身就是积累。

⚠️ 注意安全

OpenClaw 权限较大，不要给它银行、邮箱等敏感权限。初次配置建议找懂技术的朋友帮忙。

### 费用

Obsidian：**免费**。OpenClaw 软件：**免费**（开源）。唯一费用是 AI 模型调用—— 轻度使用每月约 **70-200 元人民币**。如果你用大厂的coding plan还会更便宜。可以用便宜模型日常整理，贵模型做深度分析，灵活控制成本。

· · ·

结语

知识管理的负担，该由 AI 来扛了
-----------------

Karpathy 在文末写了一句话，我觉得是全文最有力的一句：

人类的工作是策划来源、引导分析、提出好问题、思考意义。  
AI 的工作是其余所有事情。

—— Andrej Karpathy，《LLM Wiki》

我们之所以一次次放弃笔记软件、放弃知识管理，不是因为我们懒，而是因为这件事本不该由人类来做。摘要、分类、链接、查重、更新——这些机械性的苦力活，AI 比我们做得好一万倍。

而现在，工具已经就位了。Obsidian 负责展示，OpenClaw 负责干活，你负责思考。

**你的第一步，就是往 raw/ 文件夹里丢进第一篇文章。** 

* * *

### 📚 信息来源

1. Andrej Karpathy - LLM Wiki  

https://gist.github.com/karpathy/13f01326175e432c7e6a7e8d86a14c21  

2. Obsidian - 知识管理工具  

https://obsidian.md  

3. OpenClaw - AI 自动化框架  

https://docs.openclaw.ai

觉得有用？转发给也在学习的朋友 🙌  
点个「在看」，下次更新不迷路