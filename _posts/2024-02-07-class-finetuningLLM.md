---
layout: post
title:  "课程笔记 - Finetuning Large Language Models"
date:   2024-02-07 00:00:00 +0800
# categories: Python, PyQt5
published:  False
---

课程来源：Coursera

课程名称：Finetuning Large Language Models

本课程的[其他笔记](https://blog.csdn.net/weixin_39653948/article/details/132954262)

---

# **WHY FINETUNE**

## 什么是 finetune

将通用模型调整为专用模型，如专用于对话的 ChatGPT，专用于代码补全的 Copilot.

![什么是finetune](https://raw.githubusercontent.com/KeithBH/KeithPictures/main/WhatIsFinetuning.png)

## Finetune 与 Prompt 工程的区别

* 输入数据量更大
* 模型能够学习

![finetuning_vs_prompteng](https://raw.githubusercontent.com/KeithBH/KeithPictures/main/Finetuning_vs_PromptEng.jpg)

## Finetune 有什么用？

* 提升输出的一致性；
* 减少幻觉；
* 将模型客制化为指定用途；
* 过程类似早期训练过程

### 训练自己的模型可以

* 保证隐私；
* 使用更小的模型达到相同的效果以节省成本；
* 缩短响应时间；
* 定制输出风格

## 用于进行 finetune 的工具

由低级到高级排序：

* PyTorch
* HuggingFace
* Llama Library

有意思的是，[这篇文章](https://zhuanlan.zhihu.com/p/675100643)指出，llama 库只是 lamini 的套壳。

## 实操：对比 finetune 前后的模型

课程可以直接使用 Jupyter Notebook 运行代码；我尝试在本地配置环境后运行 .py 脚本。

```python
import os
import lamini

lamini.api_url = os.getenv("POWERML__PRODUCTION__URL")
lamini.api_key = os.getenv("POWERML__PRODUCTION__KEY")

# from llama import BasicModelRunner
# 按照前文的说法，此处使用 lamini 而不是 llama

non_finetuned = BasicModelRunner("meta-llama/Llama-2-7b-hf")
non_finetuned_output = non_finetuned("Tell me how to train my dog to sit")
print(non_finetuned_output)
```

TODO: 了解 `lamini` 及其用法。

---

# **WHERE FINETUNING FITS IN**

## 预训练

### 什么是预训练

在预训练之前，模型完全没有知识，不能输出英文单词。预训练使用从网络上爬取的海量数据进行**自监督**学习，这些数据经过清洗，但是没有标签。预训练的目的是使模型具备预测下一个 token 的能力。

预训练是一个费钱且费时的工作，闭源模型的预训练过程不会被公开。存在诸如 The Pile 之类的开源数据集。

### 预训练的局限性

下图举例说明了预训练的局限性，即训练数据中可能有一道地理题，在使用该数据进行训练后，给模型输入“墨西哥的首都在哪里”，得到的输出是“匈牙利的首都在哪里”。显然，这并不是理想的输出。

![预训练的局限性](https://raw.githubusercontent.com/KeithBH/KeithPictures/main/limitation_of_pretrained_model.png)

## Finetune

### 什么是 finetune

进一步训练。

相比于预训练需要的数据量小很多。可以像预训练一样自监督学习，也可以使用人工标注的数据。

微调会升级整个模型（而不是模型的一部分），微调与预训练的目标相同，都是提升模型预测下一个 token 的能力。

### Finetune 起到了什么作用

改善模型的行为、使模型获得新知识

### 需进行 finetune 的任务

文字输入，文字输出。

可以分为两种，概括和扩写，即输入少输出多和输入多输出少。

### 衡量 finetune 效果的指标

任务明确性（Task Clarity）。讲了一堆还是人来判断结果的好坏。

### 推荐的第一次 finetune 的做法

![推荐的第一次 finetune 的做法](https://raw.githubusercontent.com/KeithBH/KeithPictures/main/First_time_finetuning.png)

推荐的数据量：1K

## Finetune 用到的数据
### 查看预训练使用的 Common Crawl 数据集

```python
import jsonlines
import itertools
import pandas as pd
from pprint import pprint
import datasets
from datasets import load_dataset # huggingface 的用于加载数据的库

# 查看预训练使用的 Common Crawl 数据集
# 地址：https://huggingface.co/datasets/c4
# 经过实测，可能需要科学上网才能获取该数据集
pretrained_dataset = load_dataset("c4", "en", split="train", streaming=True) # 由于数据量非常大，需要指定 streaming=True
n = 5
print("Pretrained dataset:")
top_n = itertools.islice(pretrained_dataset, n)
for i in top_n:
  print(i)
```

运行上述代码，得到的数据集内容如下：

```Python
Pretrained dataset:
{'text': 'Beginners BBQ Class Taking Place in Missoula!\nDo you want to get better at making delicious BBQ? You will have the opportunity, put this on your calendar now. Thursday, September 22nd join World Class BBQ Champion, Tony Balay from Lonestar Smoke Rangers. He will be teaching a beginner level class for everyone who wants to get better with their culinary skills.\nHe will teach you everything you need to know to compete in a KCBS BBQ competition, including techniques, recipes, timelines, meat selection and trimming, plus smoker and fire information.\nThe cost to be in the class is $35 per person, and for spectators it is free. Included in the cost will be either a t-shirt or apron and you will be tasting samples of each meat that is prepared.', 'timestamp': '2019-04-25T12:57:54Z', 'url': 'https://klyq.com/beginners-bbq-class-taking-place-in-missoula/'}
{'text': 'Discussion in \'Mac OS X Lion (10.7)\' started by axboi87, Jan 20, 2012.\nI\'ve got a 500gb internal drive and a 240gb SSD.\nWhen trying to restore using disk utility i\'m given the error "Not enough space on disk ____ to restore"\nBut I shouldn\'t have to do that!!!\nAny ideas or workarounds before resorting to the above?\nUse Carbon Copy Cloner to copy one drive to the other. I\'ve done this several times going from larger HDD to smaller SSD and I wound up with a bootable SSD drive. One step you have to remember not to skip is to use Disk Utility to partition the SSD as GUID partition scheme HFS+ before doing the clone. If it came Apple Partition Scheme, even if you let CCC do the clone, the resulting drive won\'t be bootable. CCC usually works in "file mode" and it can easily copy a larger drive (that\'s mostly empty) onto a smaller drive. If you tell CCC to clone a drive you did NOT boot from, it can work in block copy mode where the destination drive must be the same size or larger than the drive you are cloning from (if I recall).\nI\'ve actually done this somehow on Disk Utility several times (booting from a different drive (or even the dvd) so not running disk utility from the drive your cloning) and had it work just fine from larger to smaller bootable clone. Definitely format the drive cloning to first, as bootable Apple etc..\nThanks for pointing this out. My only experience using DU to go larger to smaller was when I was trying to make a Lion install stick and I was unable to restore InstallESD.dmg to a 4 GB USB stick but of course the reason that wouldn\'t fit is there was slightly more than 4 GB of data.', 'timestamp': '2019-04-21T10:07:13Z', 'url': 'https://forums.macrumors.com/threads/restore-from-larger-disk-to-smaller-disk.1311329/'}
{'text': 'Foil plaid lycra and spandex shortall with metallic slinky insets. Attached metallic elastic belt with O-ring. Headband included. Great hip hop or jazz dance costume. Made in the USA.', 'timestamp': '2019-04-25T10:40:23Z', 'url': 'https://awishcometrue.com/Catalogs/Clearance/Tweens/V1960-Find-A-Way'}
{'text': "How many backlinks per day for new site?\nDiscussion in 'Black Hat SEO' started by Omoplata, Dec 3, 2010.\n1) for a newly created site, what's the max # backlinks per day I should do to be safe?\n2) how long do I have to let my site age before I can start making more blinks?\nI did about 6000 forum profiles every 24 hours for 10 days for one of my sites which had a brand new domain.\nThere is three backlinks for every of these forum profile so thats 18 000 backlinks every 24 hours and nothing happened in terms of being penalized or sandboxed. This is now maybe 3 months ago and the site is ranking on first page for a lot of my targeted keywords.\nbuild more you can in starting but do manual submission and not spammy type means manual + relevant to the post.. then after 1 month you can make a big blast..\nWow, dude, you built 18k backlinks a day on a brand new site? How quickly did you rank up? What kind of competition/searches did those keywords have?", 'timestamp': '2019-04-21T12:46:19Z', 'url': 'https://www.blackhatworld.com/seo/how-many-backlinks-per-day-for-new-site.258615/'}
{'text': 'The Denver Board of Education opened the 2017-18 school year with an update on projects that include new construction, upgrades, heat mitigation and quality learning environments.\nWe are excited that Denver students will be the beneficiaries of a four year, $572 million General Obligation Bond. Since the passage of the bond, our construction team has worked to schedule the projects over the four-year term of the bond.\nDenver voters on Tuesday approved bond and mill funding measures for students in Denver Public Schools, agreeing to invest $572 million in bond funding to build and improve schools and $56.6 million in operating dollars to support proven initiatives, such as early literacy.\nDenver voters say yes to bond and mill levy funding support for DPS students and schools. Click to learn more about the details of the voter-approved bond measure.\nDenver voters on Nov. 8 approved bond and mill funding measures for DPS students and schools. Learn more about what’s included in the mill levy measure.', 'timestamp': '2019-04-20T14:33:21Z', 'url': 'http://bond.dpsk12.org/category/news/'}
```

### 查看将用于 finetune 的数据集

```Python
# 暂未尝试本地运行
filename = "lamini_docs.jsonl"
instruction_dataset_df = pd.read_json(filename, lines=True)
instruction_dataset_df
```

### 格式化数据的几种方式
####