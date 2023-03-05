# Octopus Deploy 2018 版本变更- Octopus Deploy

> 原文：<https://octopus.com/blog/version-change-2018>

几天前，Paul 发布了一个关于 Octopus Deploy 2017 年的回顾，随后是我们 2018 年的[路线图。在这篇文章中，我将讨论为什么我们决定将 Octopus Deploy 的版本策略与每月发布的节奏保持一致。](/blog/roadmap-2018)

但是与其花太多的时间来描述原因和好处，我想描述一下我们是如何走到这一步的——也许这对你也有帮助？

[![Roadmap for 2018](img/3208f0daeb55ba8e833a207a245d51bf.png)](#)

## 我们正在改变什么

不多，真的。下面是我们计划改变的简要总结:

*   我们将在 2018 年发布第一版 Octopus `2018.1`，而不是在几天后发布 Octopus `4.2`
*   尽管从`4.x`到`2018.x`的跳跃可能看起来意义重大，但除了我们计划作为章鱼`4.2`发布的新功能之外，代码并没有从章鱼`4.1`发生重大变化
*   **定价和许可保持不变**
*   我们仍计划每月发货一次
*   我们将在每个日历年的第一次发布时删除版本的主要部分(第一个数字)
*   我们将在每月发布的节奏上增加版本的次要部分(第二个数字);除非我们因为某些原因跳过了一个月
*   我们仍然会在这个月发布**补丁**,包括一些小的改进和错误修复

## 去了又回来

改变我们的版本策略的决定实际上是我们作为一个软件产品公司发展的副产品，我认为值得分享一些故事，以防对您的情况有所帮助。

我们喜欢用实验的方法来经营我们的公司。我们不会纯粹假设新的方式会比旧的方式更好，或者盲目地跟随他人的脚步来做出决定，而是花时间来反思我们过去所做的改变，并决定如何从那里进行有机的迭代。我们最好用某种可量化的指标来做这件事。找到最适合我们的可能需要更长的时间，但是最大的成功是:**我们理解*为什么*我们以我们的方式做事**。转述一下[切斯特顿栅栏](https://en.wikipedia.org/wiki/Wikipedia:Chesterton%27s_fence)的负责人:

> 在你拆掉围墙之前，首先要明白为什么要把它放在那里。

如果 G. K .切斯特顿是 2018 年的开发者，他可能会说:

> 在你阅读 git 历史之前，不要拆掉围墙！

也许我们故事的一部分会对你自己的情况有所帮助？

### 版本化事物

决定如何对事物进行版本化证明是一个比我最初设想的更棘手的问题。一路走来，我们尝试了:

*   从`0.1`开始，从那里开始做当时觉得正确的事情
*   对所有事情使用严格的 [SemVer](https://semver.org) ！
*   区分“产品版本化”(版本更多地与营销和沟通联系在一起)和“组件版本化”(遵循语义版本化)
*   让版本反映每月和每年的节奏，中间有补丁

每种方法都有一些优点和一些缺点。

### 做当时觉得正确的事

从 Octopus `1.x`到`2.x`再到`3.x`的变化都是合理的:我们做了大的架构改变，增加了主要功能，有时还会破坏兼容性。

在`3.0`之后，我们在`3.3`之前发布了几个特性版本，并最终致力于构建[对多租户部署的一流支持](https://octopus.com/docs/deployments/patterns/multi-tenant-deployments)。在某个时间点，我们承诺在 Octopus `3.4`中发布多租户部署，并坚持使用该版本。回想起来，我认为这个版本应该是章鱼`4.0`。这是对产品及其功能的重大改变，从开始到结束花了六个月的时间。

在许多方面，这种方法是可行的，但它也让人感觉非常随意，没有一套清晰的指导方针来推动我们的决策。这导致了大版本变化时的一些内部紧张，并使我们的版本不可预测。

### 高度自治和永久自治

多租户部署是一种入侵性的变化，它就像一个代码坝，阻碍了其他功能，直到它完成，因为一切都开始依赖于这些代码变化。在那次经历的基础上，我们决定让团队在高度自治的情况下工作，一完成就把较小的功能独立地发布给彼此。

我们还想使用一种语义版本化的形式来帮助指导我们决定每个版本的版本应该是什么样子。我们为 Octopus Deploy 产品采用了这个策略，我们的每个库和其他组件(比如触手)都将使用语义版本控制。

同样，这种方法通常适用于版本控制，但是我们发现我们的团队过于独立。我们最终运送 Octopus `3.9`和`3.10`仅相隔几天，一周后又运送 Octopus `3.11`。

[![Octopus 3.9, 3.10, and 3.11 merely days apart](img/713cd16936d74950541ee3a5882df945.png)](#)

就其本身而言，我们并不认为这是一个问题——代码很好，而且这些变化对我们和我们的客户都很重要...但是我们已经优化以减少内部摩擦，代价是外部的可预测性和我们讲述一个有凝聚力的产品故事的能力。

#### 营销和沟通受到影响

我们是如此自主地工作，摩擦如此之少，以至于我们团队的一半人甚至没有意识到我们已经达到了`3.11`，并且我们已经为[发布了管理和部署 X.509 证书的特性](https://octopus.com/docs/deployments/certificates)——可以说这是 Octopus 能为你做的最好的事情之一——而我们并没有真正充分利用这个机会来宣扬它！同时，我们在类型化变量上犯了一个小错误，两个团队在解决同一个问题时采用了稍微不同的方法。

这不是版本问题，这是一个**计划**问题！我们运送的东西真的很好，但我们并没有刻意保持凝聚力和一致性。

### 开始节奏

2017 年 4 月，我们承诺从 [Octopus Deploy 3.12](/blog/octopus-april-release) 开始，每月发布一个新的 Octopus Deploy“功能”版本。在那篇文章中:

> 这意味着我们将按照您可以信赖的可预测的时间表发布新版本。这些版本将包括新的特性，以及当月所有补丁的汇总。我们做这个实验的目的如下:

> **注意**:我们仍然会继续在补丁中发布小的改进和错误修复，只要它们准备好了。我们希望尽快将这些改变交到你们手中，这样就不会改变。

自 2017 年 4 月以来，我们每月大约在同一时间发布一个新功能版本。我们认为它帮助我们更好地规划对产品的更小的、增量的和有价值的改变。

这种节奏有助于我们更好地计划，但它不是灵丹妙药。每个团队会自主地找到他们能创造的最高价值的东西，并着手去创造它们。在每个月初，我们会查看哪些产品即将发布，然后为该版本构建一个有凝聚力的故事。我们有几个月没有准备好发布，所以我们推迟了几周发布。

使用这种方法，我们发布了 Octopus `3.12` - `3.17`所有有价值的功能，最终当我们在一个大版本中发布了[新用户界面](/blog/octopus-release-4-0)和[一大堆其他有价值的功能](/blog/octopus-v4-blog-series-kickoff)时，我们升级到了`4.0`。

### 一个缺失的部分:故意排列

我故意用故意这个词。我们最终发布了一些非常好的版本，这些版本的内聚性更多的是一个快乐的意外，而不是刻意的设计。2017 年底，我们开始思考下一个有机步骤。我们真的希望 Octopus Deploy 在 2018 年向拥抱 DevOps 文化的人们讲述一个有凝聚力的相关故事。

我们的每个团队仍然在高度自治的情况下工作，但随着 2018 年的进展，我们已经迭代到每个团队都在努力讲述一个有凝聚力的故事的地方。

## 结论

没有太多变化。**定价和许可保持不变。**我们只是将我们的版本号与我们的月度和年度节奏保持一致。这意味着我们将不再使用我们的主版本号来传达推断的含义，就这样。现在，我们被迫对产品进行更小、更多的增量更改，这对每个人都有好处。

无聊的部分结束了，我认为这篇文章的真正结论是:**持续交付是变革的高效代理**。通过继续信奉我们公司自己的核心价值观之一，我们多次重新审视我们的版本战略，并从根本上改变了我们规划、设计、构建和交付我们自己的软件的方式。