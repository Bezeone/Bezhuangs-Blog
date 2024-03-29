---
title: 正确认识 ChatGPT
date: 2023-04-22
tags: [2023-ML]
categories: Artificial Intelligence
references: 
  - title: 李宏毅 2023 春机器学习课程
    url: https://speech.ee.ntu.edu.tw/~hylee/ml/2023-spring.php
---

> 吴恩达说：AI 是最新的电力，大约在一百年前，我们社会的电气化改变了每个主要行业，从交通运输行业到制造业、医疗保健、通讯等方面，如今我们见到了 AI 明显的令人惊讶的能量，带来了同样巨大的转变。而在 AI 的各个分支中，发展的最为迅速的就是深度学习。去年初时，我尝试学习过[动手学深度学习](/动手学深度学习/)课程，但是没坚持下来。这次选择李宏毅 2023 年春季最新的机器学习课程，这门课专注于深度学习领域，和最新技术的应用。以下为我在学习第一讲：正确认识 ChatGPT 时所做的笔记，可供参考。

<!--more-->

### 一、对 ChatGPT 的常见误解

常见误解 1：是由开发者准备好的罐头回应。但实际上，[Chat GPT](https://chat.openai.com/chat) 每次输出都不相同。

常见误解 2：是 ChatGPT 从网上搜寻答案，整理重组给你想要的答案。但实际上，多数 ChatGPT 的答案在网络上都找不到一模一样的句子，甚至很多是幻想出来的。官方也给出了回应，说 ChatGPT 是没有连网的。

ChatGPT 真正在做的事情是文字接龙，可以把它理解成一个函数，输入一些东西就输出一些东西。输入一个句子，输出的是接下来的一个词汇出现的几率，然后从这个几率分布中做取样，所以它每次产生的答案是有随机性的。

![](https://blog.zhuangzhihao.top/img/ChatGPT01.png)

这个函数非常复杂，可能有 1700 亿个以上的参数。作为对比，$f(x) = a x + b$ 有两个参数。

这么一个复杂且神奇的函数是通过大量网络上的资料以及人类的指导下，训练出来的，当神奇函数 $f$ 找到后，ChatGPT 就不需要联网了。我们平常使用的时候，就是**测试**，测试的时候就不需要上网搜集资料了。

### 二、ChatGPT 背后的关键技术——预训练（Pre-train）

预训练（Pre-train）又叫自督导式学习（Self-supervised Learning），训练出的模型又叫基石模型（Foundation Model）。

GPT = Generative Pre-trained Transformer。

一般机器是怎样学习的？以一个英文翻译成中文为例，我们需要提供大量的成对的句子，提供给机器：I eat an apple <-> 我吃苹果，You eat an orange <-> 你吃橘子。这种学习称为督导式学习，有了成堆资料机器会自动找到函数。

然而要将一般的机器学习步骤运用在 ChatGPT 上，我们需要给它提供大量的学习资料，但人类老师提供的资料也许是不足够的，当有人问到它之前没有遇到过得问题，那么它也无法回答。

实际上，网络上的每一段文字，都能形成成对的问答，可以无痛制造成对资料。

![](https://blog.zhuangzhihao.top/img/ChatGPT02.png)

在没有人类老师指导的情况下，学习大量网络上的数据，此时称之为预训练（自督导式学习），在多种语言上做预训练后，只要教某一个语言的某一个任务，自动学会其他语言的同样任务。

之后在人类老师的指导下（督导式学习）模型可以继续学习，我们称之为微调（finetune）。当人类老师比较懒不想教 AI 的时候，或者人类老师也不知道标准答案的时候，就可以使用增强式学习（Reinforcement Learning，RL）这个时候我们只需要点个赞，或者点个踩就可以，比较省事。

### 三、ChatGPT 带来的研究问题

1.   如何精准提出需求：当我们不能精准提出需求的时候，ChatGPT 不能给出有效的答案，我们需要对 ChatGPT 进行“催眠”（调解），这在学术界叫做 Prompting。
2.   如何更改错误。ChatGPT 的预训练资料只有到 2021 年。如何让 ChatGPT 修改一个错误，并且不会导致其他错误，这是一个新的主题，叫做：Neural Editing。
3.   如何用模型侦测一段文字是不是 AI 生成的？同样的概念可以被用在语音、影像上。
4.   有时候我们不小心告诉它一些东西，有没有办法让它遗忘呢？这是一个新的研究主题，这个主题叫做：Machine Unlearning。

### 四、用 ChatGPT 玩文字冒险游戏

文字冒险游戏又叫互动式小说。

催眠指令 + ChatGPT 产生的文字冒险游戏叙述 -> ChatGPT -> 产生适合 Midjourney 生成图片的文字叙述 -> Midjourney -> 产生游戏插图。
