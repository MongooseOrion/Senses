# 学术会议：关于 ChatGPT 的一些讨论

*ChatGPT 是目前非常火热的自然语言处理引擎，藉由王小捷教授的讲解，我想从学术角度记录和理解它。*

日期：2023 年 3 月 5 日

发起人：北京邮电大学 人工智能学院 王小捷

## 主要议题

  * ChatGPT 简介
  * 自然语言处理学科简介
  * GPT 模型发展过程简介
  * GPT3.5 的特殊能力

## ChatGPT 简介

ChatGPT 是一款由 OpenAI 团队开发的大型语言模型。它是一种人工智能程序，能够用自然语言与用户进行交互和回答问题，其功能包括但不限于：

  * 回答各种问题，例如常识性问题、学科问题和生活问题等；
  * 提供建议和指导，例如职业建议、健康建议等；
  * 支持对话，可以与用户进行聊天；
  * 提供翻译服务，能够将一种语言翻译成另一种语言。

其通过从大量的文本数据中学习，从而获得处理多种语言的能力，并且在某些领域中拥有相当高的知识水平。

ChatGPT 是一个可交互的生成式预训练语言模型，其发展阶段经过下述过程：

  * GPT（2018年）：基于 Transformer 解码器的生成式预训练语言模型；
  * GPT-2（2019年）：基础结构微调，强调无监督语言模型学习，训练数据、模型规模扩大；
  * GPT-3（2020年）：基础结构未变，探索零样本学习，进一步扩大训练数据和模型规模；
  * GPT3.5（2022年）：也称 InstructGPT，在 GPT-3 的基础上进行了大量基于人类反馈学习的探索，ChatGPT 是该模型的分支，增强了对话格式的训练；


ChatGPT 的更多内容可[点此](chat.openai.com)访问。

## 自然语言处理

自然语言处理（NLP）旨在为自然语言现象建立计算模型，以达成两个目标：

  * **科学目标**：给语言学或心理语言现象提供计算解释，从计算角度帮助揭示人类使用自然语言的奥秘；
  * **技术/工程目标**：建立机器处理语言的技术方法，赋予机器处理语言的能力，完成语言处理任务。

ChatGPT 在完成第二个目标的程度上，可以认为是达到了目前最顶级的水平。

自然语言处理学科从 21 世纪初开始迎来了计算时代，大规模机器学习和深度学习技术开始被应用于自然语言处理领域，这为 ChatGPT 的出现提供了前置条件。

自然语言处理算法经过了下述阶段的发展。

### 第一阶段：词向量表示

该算法的基本思想是将词表示为 $N$ 维实数空间的向量，也即

$$w \to (x_1,x_2, \dots , x_N) \in R^{N \times N}$$

其中 $w$ 为任一自然语句。

如果两个词的语义关系越近，则它们的词向量距离越小。

### 第二阶段：预训练语言模型

采用大规模数据训练具有大规模参数的模型。

## GPT 模型发展过程

GPT是 "Generative Pre-trained Transformer" 的缩写，是一种自然语言处理中的神经网络模型。它是由 OpenAI 团队开发的，旨在提高计算机处理自然语言的能力。

GPT 模型是一个基于 Transformer 架构的神经网络模型，具有多层的编码器和解码器，可以对输入文本进行处理并生成自然语言输出。GPT 通过预训练和微调两个步骤（Pretraining-Fineturing 模式）来完成对特定任务的处理。

**预训练阶段**，GPT 模型使用海量的文本数据进行训练，学习自然语言的语法、语义和上下文关系，从而获得通用的语言表征能力。这使得GPT模型可以理解并生成具有自然流畅度和语法正确性的文本。

**微调阶段**，GPT 模型通过在特定任务数据集上进行有监督的训练，进一步优化模型，使其能够执行特定的任务，例如问答、文本分类、自然语言生成等。

目前，GPT 模型已经发展到了第三代（GPT-3），它拥有数万亿个参数，可以生成高质量的自然语言文本，能够用于多种自然语言处理任务，是当今最先进的自然语言处理模型之一。

### GPT（第一代）

从原始的**大规模无监督词向量学习**转为**大规模文本级别无监督学习**，无监督预训练任务采用下词预测任务；而在特定任务上进行适应，即有监督模型微调。

此模型采用 12 层 Transformer 解码器的堆叠，是**面向任务的头结构**。

<div align='center'><img src='../Picture/cn/屏幕截图 2023-03-05 180939.png' alt='GPT Transformer 解码器结构图' title='面向任务的头结构[1]' height='250'/></div>

### GPT-2

当模型容量非常大且数据量足够丰富时，仅依靠无监督学习获得的语言模型已经可以完成大部分语言任务，无需再进行适应，因此可以只基于大规模数据在大规模模型上做无监督预训练，之后直接用于下游任务。

该模型的核心 Transformer 解码器和上一代相比局部微调，但**模型参数规模**从 1 亿增加到了 15 亿，包含 48 层 Transformer。同时**词表大小**从 40000 增大到了 50257，**上下文窗口**从 512 增大到 1024。

GPT-2 的训练数据由 web 自由获取变为了获取 Reddit 上的高赞文章，以避免出现暴力、色情、毒品等内容，**数据大小**由 1GB 扩展至 40GB。

经过评估，该模型在包含 LAMBADA、CBT-CN、CBT-NE、WikiText2、PTB、enWiki8、text8、1BW 等多个语言模型评估数据集上 Zero-shot（指在没有特定训练数据或指导下，模型可以在新领域或新任务上进行预测和处理的能力）结果比有监督训练的 SOTA（指在某个特定领域或任务上，目前最先进和最优秀的技术、算法或模型）结果更好。

<div align='center'><img src='..\Picture\cn\图片1.png' alt='GPT-2 语言模型评估数据集评估结果' title='GPT-2 语言模型评估数据集评估结果[2]' /></div>

其中 PLL 和 BPC 指标越小性能越好，ACC 指标越高性能越好。

尽管无监督学习在阅读理解任务上性能可以比监督学习好或持平，但在摘要、翻译、问答上的表现甚至**不及简单的监督模型**。

### GPT-3

尽管 GPT-2 在一些任务上的表现不足，但是可以看到随着数据规模增大模型性能更好的趋势。下图所示的研究显示，损失和参数存在**幂律变化关系**，同时**损失越小可以期待性能越好**。

<div align='center'><img src='..\Picture\cn\屏幕截图 2023-03-05 182352.png' alt='损失和参数存在幂律变化关系' title='损失和参数存在幂律变化关系[3]' /></div>

这意味着模型性能强烈依赖规模，包括**参数、数据和计算**等。

同时，在 [Radford2019-GPT2] 的研究中发现，GPT-2 在推断时，给 1 或 k 个样例信息比没有样例信息时能带来性能提升。

基于此，GPT-3 的预训练阶段和微调阶段训练方式进行了一些改进：

  * 预训练阶段：加入更多数据，在更大规模数据上进行[基于慢的外环梯度下降训练](https://learn.microsoft.com/zh-cn/training/modules/introduction-to-classical-machine-learning/6-gradient-descent)，模型参数规模从 **15 亿到 175 亿**，数据规模从 **40GB 到 500GB**；
  * 微调阶段：在 1 个或几个样例上进行 [In-context Learning](https://zhuanlan.zhihu.com/p/484999828)，以激活目标 context 推断，这种模型训练方法允许模型在运行时动态地从输入文本中学习并调整模型参数，与有监督模型微调不同，**In-context Learning 不需要大量标注数据和预训练模型，可以在无监督的情况西训练模型**。

<div align='center'><img src='..\Picture\cn\图片2.png' alt='In-context Learning' title='In-context Learning[4]' height='300'/></div>

显然，GPT-3 从 Zero-Shot 转变为了 few-shot 的 in-context learning，下图展示了**不同规模下的 context 数据量、样例数量与准确性的关系**。

<div align='center'><img src='..\Picture\cn\屏幕截图 2023-03-06 165339.png' alt='不同规模下的 context 数据量越多准确性越强' title='不同规模下的 context 数据量、样例数量与准确性的关系[4]' height='270'/></div>

与监督学习的模型比较，Few-shot 的性能超过 fine-tuned BERT，但是比有监督训练的 SOTA 差距仍然比较大。

<div align='center'><img src='..\Picture\cn\屏幕截图 2023-03-06 170330.png' alt='在 SuperGLUE 数据集上的实验性能比较' title='在 SuperGLUE 数据集上的实验性能比较[4]' height='300' /></div>

### GPT3.5

为实现 [HHH 原则](https://zhuanlan.zhihu.com/p/597586623)，避免大规模语言模型（LLM）生成不可预测的有害内容，GPT3.5 的主要工作是在 GPT-3 上进行基于人类反馈的强化学习（Reinforcement learning from human feedback, RLHF），包含下述三个阶段：

  1. 有监督微调（Supervised Fine-tuning, SFT）：基于 “Prompt-结果示例”（通过提供一些“prompt”，即输入序列或者问题，以及期望的“结果示例”，即模型需要生成的输出序列或者答案，来训练模型）对模型进行训练；
  2. 构建奖励模型（Reward Model，RM）：基于比较数据训练 RM，RM 为后续 RL（Reinforcement Learning，RL）提供奖励值；
  3. 基于近端策略优化（Proximal Policy Optimization，PPO）的强化学习（RL）：基于 RM 提供的奖励值，采用 PPO 对第一阶段获得的模型进一步训练。

为构建 GPT3.5，必须从包含标注人员（labeler）和 Prompt 数据集在内的多个方面进行筛选和训练。

首先，labeler 需要具备敏感语言一致性、排序一致性等，以构建共同的价值观，以便有监督微调的一致性。

而 Prompt 数据库的构建，包含有三个来源：
  * labeler 写的：任意任务、每个任务有若干个不同的 Prompt、依据等待列表中的应用想、每个 Prompt 都给出结果示例；
  * 用 Labelers 写的部分 Prompt 和结果训练 GPT-3 得到的初始GPT3.5 模型，在 Playground 上开放试用时，Customer提供的；
  * 提交给 OpenAI API 的。

<div align='center'><img src='..\Picture\cn\屏幕截图 2023-03-06 191850.png' alt='Prompt 数据库组成的三个不同的数据集用于三个不同阶段' title='Prompt 数据库组成的三个不同的数据集[5]' /></div>

### ChatGPT

ChatGPT 基本采用 GPT3.5 中所积累的技术，属于 GPT3.5 模型的分支。

与 GPT3.5 不同的地方在于，ChatGPT 对对话格式进行了针对式的训练。这种**在大规模数据上预训练使得模型产生很强的语言生产能力**以及**在少量精心标注的数据下反复交互微调控制模型**的方式，使得 ChatGPT 有很强的对话能力。

ChatGPT 有效综合运用了迄今为止的各种 NLP 技术，例如早些时候的词向量化、N-gram 语言模型、Transformer 解码器等以及近年来的 IFT（Instruction FineTuning，由 Google 提出）、RLHF（由 Google/Anthropic 提出）。

### GPT-4
*该模型在北京时间 2023 年 3 月 15 日凌晨发布，未在该会议上被提到。*


## 构建 GPT 模型的一些先进技术

### 任务泛化能力

IFT 带来了较强的任务泛化能力。利用多个不同任务的训练任务进行 IFT 可以大幅提升在未见任务上的 Zero-shot 性能。

<div align='center'><img src='..\Picture\cn\屏幕截图 2023-03-07 142410.png' alt='GPT3.5 在未见任务上有出色的 Zero-shot 性能' title='GPT3.5 在未见任务上的 Zero-shot 性能[6]' height='170' /></div>

下图是定量分析任务泛化能力

<div align='center'><img src='..\Picture\cn\屏幕截图 2023-03-06 193306.png' alt='' title='定量分析任务泛化能力[6]' height='170' /></div>

### 对模型行为进行基于人类反馈的约束

RL 是复杂行为学习的有效方法，但是简单定义的奖励函数难以满足人类偏好。因此，可以引入**人类反馈信息**来获得人类偏好的奖励函数。

<div align='center'><img src='..\Picture\cn\屏幕截图 2023-03-07 140038.png' alt='引入人类反馈信息来获得人类偏好的奖励函数' title='引入人类反馈信息来获得人类偏好的奖励函数[7]' height='170' /></div>

利用这一方法设计的模型，在 Atari 游戏上取得了更好的性能，并能够学习新的复杂行为。

下述图片表明了 RLHF 对 HHH 中的有帮助性（Helpful）和无害性（Harmless）的帮助。

<div align='center'><img src='..\Picture\cn\屏幕截图 2023-03-07 140815.png' alt='RLHF 对 Helpful 和 Harmless 的帮助非常大，但[8]并未涉及对 Honest 的考察' title='RLHF 对 Helpful 和 Harmless 的帮助[8]' height='270' /></div>

## 总结

### 第一个方面
ChatGPT 目前仍存在各类问题与挑战（例如假消息和滥用情况），或者说是 LLM 行业仍然面临着各种挑战，这需要从技术和伦理多方面来进行应对。同时研发类似技术时，更应在基础阶段就进行深入的调研和研究，从“源头”来研究。

2021 年 5 月，CSET 发布了一个报告，其利用 GPT-3 模型生成 6 个虚假信息相关的任务，结果如下：

<div align='center'><img src='..\Picture\cn\屏幕截图 2023-03-07 143913.png' alt='CSET 利用 GPT-3 模型生成 6 个虚假信息相关的任务' title='CSET 利用 GPT-3 模型生成 6 个虚假信息相关的任务[9]' height='' /></div><br>

可能生成虚假信息是目前的技术内在局限性导致的：
  * ChatGPT 预训练时是用大规模网络语言文本作为数据，这里面可能含有事实正确的语言，但也可能含有错误的、虚假的、想象的、编撰的各种内容的语言；
  * ChatGPT预训练时关注的是语言特性，目前典型的训练任务是**基于前面几个词预测后面一个词，而不会关注这些语言内容是错误的、虚构的**，因此，它并没有得到这方面能力的训练；
  * ChatGPT微调时（包括后面对齐时）主要关注如何让模型有用和安全地响应人类指令，并没有将内容的真假作为一项广泛的需求放在里面。

可以尝试从以下两个方面解决：
  * 从训练材料上入手：真的和假的信息都进行标注，然后进行训练；
  * 更新学习模型和技术：判别学习/回报学习/奖惩学习/价值观学习。

### 第二个方面

从 ChatGPT 来看，大模型方面还有很多可以深入研究的内容：

#### 大模型核心单元的研究
  * 除了 FNN-CNN/RNN-Transformer，还有什么更有效的基础构件？
  * 对数学性质的研究和神经网络混沌的研究

#### 大模型体系结构的研究

  * 组合元件和组合方式的基础理论和实践指南
  * 单元交互方法、集成运算方法的理论模型

#### 大模型训练方法研究
  * 已有方法的收敛性质、收敛效率的理论保证
  * 新的训练方法探索：Forward-Forward 算法（FF）、实时交互的方法

#### 大规模高质量数据构建研究
  * 语言数据质量的定量评估指标与评估方法

### 第三个方面
在 ChatGPT 发布的第二天，2022 年 12 月 1 日，在 NeurIPS2022 年会上，图灵奖得主 Geoffrey E. Hinton 发表主题演讲《The Forward-Forward Algorithm for Training Deep Neural Networks》，提出 FF 算法。

目前在几乎所有神经网络模型中都使用误差反向传播技术（Backpropagation，BP）进行学习，但是神经科学表明：人脑中可能并不存在误差反向传播的情况。而 FF 只进行两次前向过程，避免 BP 中的反向传播。前向网络可能更合理地接近现实生活中在大脑中发生的情况
。同时，没有反向微小信号的传播需求，就降低了对运算精度的要求，降低计算能耗。


<br> **最后，不可否认的是，ChatGPT 是人工智能领域理论方法、技术实施和工程落地应用的典范，是一个里程碑式的进展，影响范围涉及社会经济文化各个领域。而构建 ChatGPT 类应用带来了一系列需要应对的技术与伦理挑战，这意味着对 ChatGPT 的研究不仅要针对 ChatGPT 本身，还要追溯其源头。同时，人工智能研究不应局限在 ChatGPT 类方法这一条路线上。**



## 相关文章
  1. Alec Radford, et al. Improving Language Understanding by Generative Pre-Training, arXiv, 2018.
  2. [Radford2019-GPT2]Alec Radford, et al. Language Models are Unsupervised Multitask Learners. 2019.
  3. [Kaplan2020]Jared Kaplan, et al. Scaling Laws for Neural Language Models. arXiv, 2020.
  4. Tom B. Brown,et al.Language Models are Few-Shot Learners. 2020NIPS.
  5. Long Ouyang, et al. Training language models to follow instructions with human feedback. arXiv2203.02155v1. 2022. 
  6. [WeiJ2022ICLR]Jason Wei, et al. FINETUNED LANGUAGE MODELSARE ZERO-SHOT LEARNERS. ICLR2022.
  7. [Christiano2017NIPS]Paul Christiano, et al. Deep reinforcement learning from human preferences. NIPS2017.
  8. [Yuntao Bai2022] Yuntao Bai, et al. Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback. arXiv2204.05862v1, 2022.
  9. Center for Security and Emerging Technology, Truth, Lies, and Automation, How Language Model Could Change Disinformation. 2021, May. 

