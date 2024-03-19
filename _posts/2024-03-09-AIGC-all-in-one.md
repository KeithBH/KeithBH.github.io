---
layout: post
title:  "Keith 对 AIGC 的汇总"
date:   2024-03-09 00:00:00 +0800
published:  True
---

# Keith 对 AIGC 的汇总

这篇 Post 作为我个人对 AIGC 的学习和持续关注的记录汇总，以收集为主，独立创作为辅。

创建于 2024-03-09，在此日期之前的内容随缘更新。

---

## 常用链接

[ChatGPT - OpenAI](https://chat.openai.com)

[Le Chat - Mistral](https://chat.mistral.ai/chat)

[HuggingChat - HuggingFace](https://huggingface.co/chat/)

[AIGC 导航 1](https://www.aigc.cn) ｜ 
[AIGC 导航 2](https://www.aigcnav.in) ｜ 
[AIGC 导航 3](https://hao.uisdc.com/ai/) 更多 AIGC 导航类网站建议直接搜索

[大模型竞技场](https://huggingface.co/spaces/lmsys/chatbot-arena-leaderboard)

[Blog - 九原山](https://ninehills.tech) LLM 学习基础教程与资料

---

## 优秀文章/资讯汇总

    结构：领域分类 - 收集日期 + 链接 + 备注;
    记录我看过/觉得有意思的文章和资讯;
    链接并不一定是原文标题，也可能是我对内容的概括;

### 文 & 文

2024-03-19 [奥特曼：GPT-5 的能力提升幅度超乎想象](https://mp.weixin.qq.com/s/Ys4KmO7S3yNzXb5mGZ1qww)

2024-03-18 [阿里数学竞赛允许硅基选手参加](https://mp.weixin.qq.com/s/06lM05sTkW1jL7J4Z9jh6Q) 数学本科一年级难度

2024-03-18 [首个 AI 程序员 Devin](https://mp.weixin.qq.com/s/xdsN3puVxa0eSC9u0E6OeQ) “发现问题、创建工单、调整代码，最好的人类开发者就是这么工作的。”；自主把任务拆解成一系列子步骤；遇到障碍自己打开对应的 Github 仓库开始查阅文档；相关项目 [MetaGPT](https://mp.weixin.qq.com/s/sxgfJf4vxvaxhO5L7-Npwg)、OpenDevin、Maisa KPU

2024-03-18 [ChatGPT 可能只有 7B 参数](https://mp.weixin.qq.com/s/y0RQ0aOrHGLzLJKxbyGxMw) 

2024-03-18 [Grok 开源](https://mp.weixin.qq.com/s/iQWMvURQ5Qgm5dJdZjv6Cw) 314B 参数，MoE 架构，Rust 语言+JAX 框架

2024-03-18 [月之暗面 Kimi 模型升级至 200 万窗口](https://mp.weixin.qq.com/s/xsBRTxJWyiI72TNrZJtJGw)

2024-03-15 [康奈尔开源近10万份审稿意见，未来论文发表或将由AI定夺](https://mp.weixin.qq.com/s/u2HVQVjAQiPO6enji_hlcQ)

2024-03-15 [Sora 作者被曝读博期间仅发表两篇论文](https://mp.weixin.qq.com/s/cqZI_nvbJv4vyw6_QCWj7A) “Sora 的两位联合负责人的博导的毕业论文附录中甚至包含了一章《伯克利周边的爬山指南》”

2024-03-15 [给训练数据打水印](https://mp.weixin.qq.com/s/jPBKfhN68zX8uT__xFAaBA) “放射性”的概念，带有水印的文本在微调过程中对模型造成污染，未细读

2024-03-15 [讨论链，多个 LLM 协作解决开放式问答挑战](https://mp.weixin.qq.com/s/guuJWxVO_vtpxI6kW0KBbQ) 多个 LLM 互动讨论，提升负责问题回答质量，未细读

2024-03-12 [小模型（sLLM）对比](https://mp.weixin.qq.com/s/fw1VyGk8keGxqRmGjz8lCA)

2024-03-09 [1Bit 量化，大模型瘦身 90%，性能保留 83%](https://mp.weixin.qq.com/s/qyzIoCyIqWDRWMBsJd1gbw) 模型压缩，推进大模型的端侧部署

2024-03-09 [Gemini 1.5 Pro 根据代码和视频 debug](https://mp.weixin.qq.com/s/ZSDCNDRu-tCkOlC9jz2j4w) 大海捞针效果良好

### 文 & 图

2024-03-18 [AI 落地营销场景](https://mp.weixin.qq.com/s/AmwN4q7FI2jopbjaj0_Tsg) 家具、模特等

### 文 & 视频

[国产 AIGC 公司 FancyTech 开始赚钱](https://mp.weixin.qq.com/s/rm_dylLhf4FP01c_hdU3Lw) AI 换装；图生视频；阿里系团队

2024-03-18 [开源复现 Open-Sora](https://mp.weixin.qq.com/s/8UQTjOph5MDRNOSwH11ZAg) DiT 架构，目测效果一般

2024-03-15 [首部 AI 制作的电影](https://mp.weixin.qq.com/s/dvbvO4pPONIrq-XWSxrR8A) 时长 90 分钟，未使用 Sora，预算为 0，[在这看](https://ainfinite.tv)

### 多模态

2024-03-19 [苹果大模型 MM1](https://mp.weixin.qq.com/s/i9bx6M32uk4Jq2KSRhv4ng)

2024-03-18 [零一万物 API 开放平台](https://mp.weixin.qq.com/s/kN_FVGHVnjba_ed5uWiCrQ) 200K 上下文；和 OpenAI API 无缝切换；还有结合 Dify 搭建应用的例子；[链接](https://platform.lingyiwanwu.com)

### AGI 进展

2024-03-18 [谷歌 SIMA 通用游戏智能体](https://mp.weixin.qq.com/s/t0a3-YMHWgE0Yb_EiV2Nuw) 支持多游戏，遵循语言指令；有潜力与任何虚拟环境互动

2024-03-12 [Claude 3 “自我认知”](https://mp.weixin.qq.com/s/KkfLI8g4afiB8a_jIjD--Q) 意识到自己在被测试

### 具身智能/人形机器人

2024-03-19 [Tracking Steamer - Vision Pro 实时训练机械狗](https://mp.weixin.qq.com/s/Zq7xxhJk14hFQ_OSTZre1g) 开源

2024-03-18 [Figure 01，OpenAI 加持的机器人](https://mp.weixin.qq.com/s/f4k8N6ebzpOH1owy-ObqEA) 效果惊艳

2024-03-15 [将试错引入大模型代理学习](https://mp.weixin.qq.com/s/dtsR5lkkELJlh0i4TzuX0Q) 通过直接与环境互动来学习和完善动作，未细读

### 汽车与AIGC

2024-03-18 [LightGPT 大模型控制红绿灯](https://mp.weixin.qq.com/s/mF9hZkkQ4aJ1cAJ1vAFV9g) 

### 其他

2024-03-19 [大模型自己优化 Prompt，及其对提示工程的影响](https://mp.weixin.qq.com/s/H6xrD2WxuXwj1tZOuYQ_Kw) “许多大公司都正在推出一个新的工作岗位：大型语言模型运营（LLMOps），该岗位的生命周期中就包含提示工程”

2024-03-19 [NVIDIA 发布 Blackwell 平台和 B200、GB200 GPU](https://mp.weixin.qq.com/s/EsFkd_isPz2J5wap6KaF5A) “可以搭建数据中心，流量带宽在一秒内就可以传输完当前整个互联网的信息量”

2024-03-19 [ChatGPT 日耗电量 ≈1.7 万家庭日耗电量](https://mp.weixin.qq.com/s/D5DR1jWBuOHphwFNiGGixQ) “奥特曼：我们需要可控核聚变”，并已押注公司 Helion；

2024-03-19 [零一万物向量数据库新 SOTA](https://mp.weixin.qq.com/s/yAyOmOr22PCVguCZm6pifw) 向量数据库是大模型长期记忆的关键基础设施；

2024-03-18 [字节级模型](https://mp.weixin.qq.com/s/BLUTwhAlbXMPKYAgIoB_0Q) 不是预测下一个 token，而是下一个字节；目标“将字节模型作为数字世界的模拟器”；**无视模态**

2024-03-15 [DUSt3R，视觉重建新 SOTA](https://mp.weixin.qq.com/s/lKHRTXT_jbivSTNo8g8EXg) 两张图重建 3D 环境，未细读

### 行业吃瓜

2024-03-09 [奥特曼无罪重返董事会！OpenAI内讧真相大白，调查结果公开](https://mp.weixin.qq.com/s/MqbgD7WjBy32dYJVRYOT-w)

2024-03-08 [OpenAI CTO Mira 可能也是赶 Altman 下台的关键人物](https://mp.weixin.qq.com/s/Iy79dT4FBjQS-oeJZvmREA)

---

## 论文

[综述：多模态大模型进化过程](https://arxiv.org/pdf/2402.12451.pdf)，还没读

---

## 上手实践

### 在 Colab 上运行 Gemma

主要参考 [Gemma7B - HuggingFace](https://huggingface.co/google/gemma-7b)

#### 问题 Repo model google/gemma-7b is gated

直接运行如下代码时

```Py
# pip install accelerate
from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("google/gemma-7b")
model = AutoModelForCausalLM.from_pretrained("google/gemma-7b", device_map="auto")

input_text = "Write me a poem about Machine Learning."
input_ids = tokenizer(input_text, return_tensors="pt").to("cuda")

outputs = model.generate(**input_ids)
print(tokenizer.decode(outputs[0]))
```

会报错 `Repo model google/gemma-7b is gated` 需要配置 access_token。参考[这篇文章](https://huggingface.co/google/gemma-7b/discussions/31)。

---

## 课程

[课程笔记：Finetuning LLM]() 链接和笔记内容还在完善中～

[何恺明 MIT 第一课：学习深度表示](https://mp.weixin.qq.com/s/OP_hSFVczszl8vc2828rUw) 还没看 :P