---
tags: 
Created: 2025-07-23 23:03
aliases: 
related: 
link:
---
> Main topic: Preliminaries

## 1 Notions

### 1.1 Starting point 出发点
- Computation Task
- Computation Model: The methods for solving these questions.


### 1.2 Related Concepts

- Representation of instance(as binary sequence): the general framework for our discussion of computational tasks (or problems)
	- The framework
	- Focus on 2 types of tasks
		- Searching solution
		- Making decision
- Model of computation: The methods for solving Computation Task

## 2 CH 1.2.1

> In mathematics and related sciences, it is customary to discuss objects without specifying their representation.

这句话的意思是：

在数学及相关科学领域，人们通常讨论的是“对象”本身的性质和关系，而**不是**它们的具体表示方式（representation）。

**举例说明：**
- 当我们讨论“整数”时，关注的是它们的加法、乘法等性质，而不是它们用十进制、二进制还是罗马数字表示。
- 讨论“图”时，关注的是顶点和边的结构，而不是它们在纸上的画法或在计算机中的存储方式。
- 研究“向量空间”时，关注的是向量之间的线性关系，而不是具体用什么坐标系或基底来表示这些向量。

**理解要点：**
- “对象”指的是数学中抽象的概念或结构。
- “表示”是指用某种具体方式（如符号、编码、图形等）来描述或实现这些对象。
- 数学更关心对象的本质属性，而不是它们的外在表现形式。

**简要总结：**  
这句话强调，数学和相关科学追求的是对对象本质的理解，而不是拘泥于它们的具体表达方式。

> Computational tasks refers to objects that are represented in some canonical way, where such canonical representation provides an “explicit” and “full” (but not “overly redundant”) description of the corresponding object.
这句话可以这样理解：

**计算任务（Computational tasks）**通常涉及对某些对象进行操作或判断。为了让计算机能够处理这些对象，我们需要用一种“标准化的方式”（canonical way）来表示它们。

- **canonical way（标准化表示）**：指的是为每种对象选定一种统一、规范的表示方法。例如，整数用二进制或十进制字符串表示，图用邻接矩阵或邻接表表示，布尔公式用特定的语法树表示等。
- **explicit and full（明确且完整）**：这种表示方法要能够完整、准确地描述对象的所有信息，没有遗漏。
- **not overly redundant（不过度冗余）**：这种表示方法不应该包含太多重复或无用的信息，避免浪费空间和计算资源。

**举例说明：**
- 一个图的邻接矩阵就是一种标准化、完整且不冗余的表示方法。
- 一个整数的二进制编码也是如此。

**简要总结：**  
这句话强调，计算任务中的对象必须用一种规范、完整、且高效（不过度冗余）的方式来表示，这样才能让计算机明确地“看到”并处理这些对象。

> In the rare cases in which one considers real numbers as part of the input to a computational problem, one actually means rational approximations of these real numbers.

这句话的意思是：

在极少数情况下，如果一个计算问题的输入包含实数（real numbers），实际上我们真正处理的是这些实数的有理数近似（rational approximations）。

**详细解释：**
- 计算机无法直接存储或处理“真正的”实数，因为实数通常有无限不循环小数部分（比如 $\pi$、$\sqrt{2}$）。
- 因此，在实际计算中，我们只能用有限精度的有理数（即分数，或者有限位小数）来近似表示这些实数。
- 所以，当计算问题的输入看似是实数时，实际上输入的是这些实数的有理数近似值（比如用小数点后若干位的数字来表示）。

**举例：**
- 计算 $\sqrt{2}$ 的平方根时，输入不会是“精确的 $\sqrt{2}$”，而是 $1.4142$ 这样的近似值。
- 处理 $\pi$ 时，输入可能是 $3.14159$，而不是“完整的 $\pi$”。

**简要总结：**  
这句话强调，计算机科学中的“实数输入”其实都是用有理数近似来代替的，因为只有这样才能在有限的计算资源下进行处理。

> One such symbol is $\perp$, which typically denotes an indication (e.g., produced by some algorithm) that something is wrong.

这句话的意思是：

符号 $\perp$（读作“垂直”或“perp”）在数学和计算机科学中，通常用来表示“出错”或“不成立”的情况。比如在某些算法或证明中，如果遇到非法输入、无法继续计算、验证失败等情形，就会输出或返回 $\perp$，以此明确表示“这里有问题”或“操作失败”。

**举例说明：**
- 在密码学协议中，如果验证者发现签名无效，可能会输出 $\perp$，表示拒绝接受。
- 在算法设计中，如果某个步骤无法进行下去，也可以用 $\perp$ 作为特殊返回值，表示异常或错误。

**简要总结：**  
$\perp$ 是一种通用的“错误标志”或“失败信号”，用来明确指出某个过程或算法遇到了问题。


## 3 CH 1.2.2 Computational Tasks

> Two fundamental types of computational tasks are the so-called search problems and decision problems. In both cases, the key notions are the problem’s instances and the problem’s specification.

这句话可以这样理解：

计算任务有两种基本类型：**搜索问题（search problems）**和**判定问题（decision problems）**。无论是哪种类型，理解这类问题的关键在于两个概念：**问题实例（instance）**和**问题规范（specification）**。

**详细解释：**

- **判定问题（decision problem）**：给定一个输入（问题实例），问题的答案是“是”或“否”（true/false）。比如：“这个数是素数吗？”、“这个图是连通的吗？”等。
- **搜索问题（search problem）**：给定一个输入（问题实例），要求找到一个满足某种条件的具体解。比如：“给定一个方程，找到它的一个解。”、“给定一个图，找到一条哈密顿回路。”等。

- **问题实例（instance）**：指的是具体的输入数据。比如“给定的某个数”、“给定的某个图”。
- **问题规范（specification）**：指的是对问题的精确定义，包括输入格式、输出要求、什么样的解是有效的等。

**简要总结：**  
这句话强调，无论是判定问题还是搜索问题，理解和描述它们时都要明确“输入是什么”（实例）和“问题到底要求什么”（规范）。

### 3.1 CH1.2.2.1 Search Problem

**Definition 1.1** (solving a search problem): Let $R \subseteq \{0,1\}^* \times \{0,1\}^*$ and $R(x) \stackrel{\text{def}}{=} \{y : (x, y) \in R\}$ denote the set of solutions for the instance $x$. A function $f : \{0,1\}^* \to \{0,1\}^* \cup \{\perp\}$ solves the search problem of $R$ if for every $x$ the following holds: if $R(x) \neq \emptyset$ then $f(x) \in R(x)$ and otherwise $f(x) = \perp$.

**定义 1.1（搜索问题的求解）：**  
设 $R \subseteq \{0,1\}^* \times \{0,1\}^*$，并令 $R(x) \stackrel{\text{def}}{=} \{y : (x, y) \in R\}$ 表示实例 $x$ 的解的集合。一个函数 $f : \{0,1\}^* \to \{0,1\}^* \cup \{\perp\}$ 被称为解决了 $R$ 的搜索问题，如果对每个 $x$ 都满足：若 $R(x) \neq \emptyset$，则 $f(x) \in R(x)$；否则 $f(x) = \perp$。

这个定义描述了什么叫“解决一个搜索问题”。

**逐句解释：**

- $R \subseteq \{0,1\}^* \times \{0,1\}^*$：  
  $R$ 是一个二元关系，表示所有“实例-解”对。每个实例和解都用二进制字符串表示。

- $R(x) = \{y : (x, y) \in R\}$：  
  对于每个实例 $x$，$R(x)$ 是所有与 $x$ 匹配的有效解 $y$ 的集合。

- $f : \{0,1\}^* \to \{0,1\}^* \cup \{\perp\}$：  
  $f$ 是一个函数，输入一个实例 $x$，输出一个解 $y$ 或特殊符号 $\perp$（表示“无解”）。

- “$f$ 解决了 $R$ 的搜索问题”意味着：  
  - 如果 $x$ 有解（即 $R(x) \neq \emptyset$），那么 $f(x)$ 必须输出其中一个有效解 $y$（$f(x) \in R(x)$）。
  - 如果 $x$ 没有解（$R(x) = \emptyset$），那么 $f(x)$ 必须输出 $\perp$，表示“无解”。

**简要理解：**  
这个定义形式化了“什么叫解决一个搜索问题”：  
- （Completeness）对于有解的实例，算法要能给出一个正确的解；  
- （Soundness）对于无解的实例，算法要能明确表示“无解”。

**总结：**  
这个定义要求，解决搜索问题的算法必须对每个实例都能正确区分“有解”与“无解”，并在有解时给出一个有效解。

### 3.2 CH1.2.2.2 Decision Problem

> A decision problem consists of a specification of a subset of the possible instances.

这句话的意思是：

**判定问题（decision problem）**的本质，就是在所有可能的输入实例中，明确规定出哪些实例属于“是”（YES）类，哪些属于“否”（NO）类。

**详细解释：**
- 所有可能的实例（inputs）组成一个全集，比如所有二进制字符串。
- 判定问题就是从这个全集中，**选出一部分实例**，这些实例被定义为“满足条件”的（即答案为“是”）。
- 换句话说，判定问题就是**指定一个实例集合**，算法的任务就是判断给定实例是否属于这个集合。

**举例：**
- 素数判定问题：所有正整数中，属于“素数”的集合就是这个判定问题的规范。
- 图连通性判定问题：所有图中，属于“连通图”的集合就是这个判定问题的规范。

**简要总结：**  
这句话强调，判定问题就是通过指定一个实例子集，来定义“哪些输入属于YES类”，算法只需判断输入是否在这个集合中。

> One important case, which corresponds to the aforementioned search problems, is the case of the set of instances having a solution; that is, for any binary relation $R \subseteq \{0, 1\}^* \times \{0, 1\}^*$ we consider the set $\{x : R(x) \neq \emptyset\}$.

有一种重要的判定问题，就是判断“某个实例是否有解”。这正好对应前面提到的搜索问题。

**详细解释：**
- 给定一个二元关系 $R \subseteq \{0, 1\}^* \times \{0, 1\}^*$，$R(x)$ 表示实例 $x$ 的所有解的集合。
- 那么，$\{x : R(x) \neq \emptyset\}$ 就是所有“有解”的实例组成的集合。
- 这个集合就是一个判定问题：输入 $x$，判断 $x$ 是否属于这个集合（即 $x$ 是否有解）。

**举例：**
- 给定一个方程组，$R(x)$ 表示所有满足方程组的解。如果 $R(x) \neq \emptyset$，说明这个方程组有解；否则无解。
- 判定问题就是：给定一个方程组，判断它有没有解。

**简要总结：**  
这句话强调，很多判定问题其实就是在判断“某个实例有没有解”，这与搜索问题密切相关。

### 3.3 Promise Problems (an Advanced Comment)

> 许多自然的搜索和判定问题，用“承诺问题”（promise problems）的术语来描述会更加贴切。在承诺问题中，可能的实例域是 $\{0,1\}^*$ 的一个子集，而不是整个 $\{0,1\}^*$。

> 特别需要注意的是，许多搜索和判定问题的自然表述其实是针对某一类特定的实例（例如，一个方程组、一对数字、一个图），而这些对象的自然表示方式只用到了 $\{0,1\}^*$ 的一个严格子集。

> 暂时我们先忽略这个问题，但会在第2.4.1节中重新讨论。这里只需指出，在典型情况下，我们可以通过假设每个字符串都代表某个合法对象来忽略这个问题（例如，对于那些在自然表示中未被使用的字符串，可以规定它们都表示某个固定的对象）。

这段话的核心意思是：

在理论计算机科学中，我们通常把所有可能的输入实例都看作是二进制字符串（$\{0,1\}^*$）。但实际上，很多具体问题（比如解方程、图论问题等）只关心某一类“合法”的输入，比如“能表示成一个图的字符串”或者“能表示成一个方程组的字符串”。这些合法输入只占所有二进制字符串的一个子集。

**Promise Problem（承诺问题）**的概念，就是专门用来描述这种“只对部分输入有意义”的问题。它允许我们只关注那些“承诺”过的、合法的输入，而不必对所有可能的二进制字符串都给出定义。

但在实际讨论中，为了简化问题，很多时候我们会假装“每个字符串都代表某个合法对象”。比如：如果某个字符串不是一个合法的图的编码，我们就规定它代表某个固定的图（比如一个空图）。这样，我们就可以暂时忽略“输入是否合法”这个细节，把所有字符串都当作有效输入来处理。

**简要理解：**
- 很多实际问题只对部分输入有意义（合法实例）。
- “承诺问题”就是只对这些合法实例提问。
- 为了方便，有时我们假设所有字符串都能代表某个对象，这样就不用区分哪些输入是合法的。
- 这个细节暂时可以忽略，后面会详细讨论。

**举例说明：**
- 比如“图的连通性”问题，只有能被解释为图的字符串才有意义。对于不能表示成图的字符串，我们可以规定它们都表示一个特殊的图，这样就不用单独处理非法输入了。

**总结：**
这段话提醒我们，虽然理论上所有输入都是二进制字符串，但实际问题往往只关心其中一部分。为简化理论分析，我们可以假设所有输入都有效，必要时再回到“承诺问题”的更精细讨论。


## 4 Uniform Models (Algorithms)

> Science is One.
> Laci Lovász (according to Silvio Micali, ca. 1990)

### 4.1 Overview and general principles
> Before being formal, let we offer a general and abstract description, which is aimed at capturing any artificial as well as natural process.

这里的 artificial process 和 natural process 指的是：

- **Artificial process（人工过程）**：指的是由人类设计、制造或控制的过程，通常包括各种算法、计算机程序、工程系统等。例如，计算机执行的排序算法、工厂的自动化生产线、机器人运动等，都是人工过程。

- **Natural process（自然过程）**：指的是自然界中自发发生的过程，不依赖于人类的直接设计或控制。例如，水的蒸发、植物的光合作用、动物的进化、天气变化等，都是自然过程。

**在原文语境下的理解：**  
作者想要给出一个“通用且抽象的描述”，这个描述既能涵盖人类设计的各种人工过程（比如算法、计算任务），也能涵盖自然界自发发生的各种自然过程。也就是说，后面要介绍的理论框架，不仅适用于人工智能、计算机科学中的问题，也适用于描述自然界中的信息处理和演化等现象。

**简要总结：**  
artificial process 指人造的、设计出来的过程；natural process 指自然界自发的过程。这里强调理论的普适性，既能描述人工系统，也能描述自然系统。

### 4.2 A concrete  Model: Turing Machines

### 4.3 Actual Model

The main component in the environment of a Turing machine is an infinite sequence of cells, each capable of holding a single symbol (i.e., member of a finite set $\Sigma \supset \{0, 1\}$).

图灵机的“环境”中最核心的部分是一个无限长的格子序列（也叫“纸带”）。每个格子（cell）都能存放一个符号，这些符号来自一个有限的符号集 $\Sigma$，而且这个符号集至少包含 $\{0, 1\}$。


#### 4.3.1 environment

**Environment** contains:
- Instantaneous configuration ^beacab
	- Tape
	- Machine's Location
	- Internal State

**Instantaneous configuration**
- current location of the machine on the sequence
- internal state of the machine which is a member of finite set $Q$

**Tape**
- the aforementioned infinite sequence of cells

**详细解释：**
- 图灵机是理论计算机科学中最基本的计算模型。
- 它有一条无限长的纸带，这条纸带被分成一个个格子（cell）。
- 每个格子里只能存放一个符号，比如 $0$、$1$ 或其他符号。
- 所有可能出现的符号都来自一个有限集合 $\Sigma$，这个集合至少要包含 $0$ 和 $1$，但也可以有更多符号（比如空格、分隔符等）。
- “无限”是指纸带理论上可以无限延伸，满足任何计算所需的空间。

**简要理解：**
- 图灵机的纸带就是它的“内存”，每个格子能存一个符号。
- 这些符号的种类有限，但纸带长度无限。
- 这是图灵机模型的基础设定。

**总结：**
这句话描述了图灵机的基本存储结构：无限长的纸带，每格存一个有限集合中的符号。

#### 4.3.2 Finite rule(i.e. finite function)

> Also called the transition function, which is defined over the set of all possible symbol-state pairs.

That is : $\varphi: \sum \times Q \to \sum \times Q \times \{-1,0,+1\}$ 
Where $\{-1,0,+1\}$ correspond to a movement instruction.

In addition, the machines description specifies 
- an initial state
- a halting state

> We stress that, in contrast to the finite description of the machine, the tape has an a priori unbounded length (and is considered, for simplicity, as being infinite).

这句话的意思是：

我们要特别强调，**与图灵机本身的有限描述不同**，图灵机的纸带在理论上是**先验地没有长度限制的**（也就是说，纸带可以无限延长）。为了简化讨论，通常直接把纸带看作是“无限长”的。

**详细解释：**

- **finite description of the machine（机器的有限描述）**  
  图灵机本身（包括状态集合、符号表、转移函数等）都可以用有限的信息完全描述清楚。也就是说，图灵机的“程序”是有限的。

- **the tape has an a priori unbounded length（纸带先验地没有长度限制）**  
  纸带是图灵机用来读写数据的“内存”。和机器本身的有限性不同，纸带在理论模型中被假设为可以无限延长——无论计算需要多少空间，都可以继续往后用。

- **for simplicity, as being infinite（为简化，视为无限）**  
  实际上，只要“足够长”就行，但为了理论分析方便，通常直接假设纸带是无限长的。

**简要理解：**

- 图灵机的“硬件和程序”是有限的，但“内存空间”（纸带）是无限的。
- 这样做是为了让模型足够强大，可以描述所有可计算的问题。
- 这种假设只在理论上成立，现实计算机的内存当然是有限的。

**总结：**  
这句话强调了图灵机模型的一个重要特点：机器本身是有限的，但纸带（内存）是无限的，这样才能保证理论上的通用性和简洁性。



#### 4.3.3 Computation step 

> A single computation step of such a Turing machine **depends on** its current location on the tape, on the contents of the corresponding cell, and on the internal state of the machine. Based on the latter two elements, the transition function determines a new symbol-state pair as well as a movement instruction (i.e., “left” or “right” or “stay”).
> The machine modifies the contents of the said cell and its internal state accordingly, and moves as directed.

这段话描述了**图灵机一次计算步骤的具体过程**，可以分为以下几个要点

计算步骤**依赖（Depends on）**哪些因素？
- **当前位置**：图灵机的读写头当前在纸带上的哪个格子（cell）。
- **当前格子的内容 $\sigma$ **：当前位置上的格子里存的是什么符号。
- **机器的内部状态 $q$**：图灵机当前处于哪一个内部状态（比如“开始”、“处理中”、“结束”等）。

**转移函数的作用**
- **转移函数（transition function）**：这是图灵机的“程序”，它根据“当前格子的内容”和“当前内部状态”这两个信息，决定接下来要做什么。
- **输出内容**：
	- **新的符号-状态对（new symbol-state pair）**：决定要把当前位置的格子改成什么符号，以及机器要进入哪个新的内部状态。
	- **移动指令（movement instruction）**：决定读写头接下来是向左移动、向右移动，还是停在原地。

**执行过程**
- 图灵机根据转移函数的指令：
  1. **修改当前格子的内容**（写入新的符号）。
  2. **改变自己的内部状态**（进入新的状态）。
  3. **移动读写头**（向左、向右或不动）。


**简要理解**

- 图灵机每一步的行为完全由“当前状态”和“当前格子的内容”决定。
- 每一步都包括：写符号、换状态、移动头。
- 这是图灵机最基本的工作方式，也是它能模拟任何算法的基础。


**总结**

这段话强调了图灵机每一步的操作流程：  
**读取当前格子的内容和当前状态 → 用转移函数查表 → 决定写什么、变成什么状态、头往哪儿动 → 执行这些操作。**  
整个计算过程就是由这样的一步步简单操作组成的。

> We comment that in most expositions, one refers to the location of the “head of the machine” on the tape (rather than to the “location of the machine on the tape”). 

这句话的意思是：

在大多数教材或讲解中，人们通常说的是“图灵机的读写头在纸带上的位置”（the location of the ‘head of the machine’ on the tape），而不是说“机器在纸带上的位置”（the location of the machine on the tape）。

---

**详细解释：**

- 图灵机本身是一个抽象的“控制器”，它有一个“读写头”（head），这个头可以在纸带上左右移动，读取或写入符号。
- 实际上，机器本体是固定的，只有“读写头”在纸带上移动。
- 所以，描述图灵机操作时，更准确的说法是“读写头的位置”，而不是“机器的位置”。
- 但有时为了简化表达，可能会说“机器在纸带上的位置”，其实指的就是“读写头的位置”。

---

**简要理解：**

- 正确的术语应该是“读写头的位置”。
- “机器的位置”其实就是“读写头的位置”的一种不严谨说法。



**总结：**  
这句话提醒我们，在描述图灵机时，应该用“读写头的位置”这个更准确的说法，因为实际上只有读写头在纸带上移动。

##### 4.3.3.1 successive configuration function

> Formally, we define the **successive configuration function** that maps each [[Textook-Ch1.2 Computational Tasks and Models#^beacab | instantaneous configuration]] to the one resulting by letting the machine take a single step. This function modifies its argument in a very minor manner, as described in the foregoing; that is, the contents of at most one cell (i.e., at which the machine currently resides) is changed, and in addition the internal state of the machine and its location may change, too.

这句话的意思是：

**我们正式地定义了“后继配置函数”（successive configuration function）**，它的作用是：把每一个“瞬时配置”（instantaneous configuration）映射到经过图灵机一步操作后得到的新配置。

详细解释
- **瞬时配置（instantaneous configuration）**：指的是图灵机在某一时刻的完整状态，包括纸带上所有格子的内容、读写头的位置、机器的内部状态。
- **后继配置函数**：这是一个函数，输入是当前的瞬时配置，输出是图灵机执行一步操作后得到的新的瞬时配置。


这一步操作会带来哪些变化？
- 这个函数对输入的配置只做了**很小的修改**（in a very minor manner）：
  - **最多只会改变一个格子的内容**，也就是当前读写头所在的那个格子。
  - **机器的内部状态**可能会改变（比如从“状态A”变到“状态B”）。
  - **读写头的位置**也可能会改变（比如向左、向右或不动）。

重点理解
- 每一步操作只会影响很有限的部分：一个格子的内容、机器的状态、读写头的位置。
- 纸带上其他格子的内容都不会变。
- 这种“局部性”是图灵机模型的一个重要特征。

##### 4.3.3.2 Initial environment (Initial Config)

- Machine residing in the first (leftmost) cell
- Initial state
#### 4.3.4 A philosophical comment

>The fact that a thesis is used to link an intuitive concept to a formal definition is common practice in any science (or, more broadly, in any attempt to reason rigorously about intuitive concepts).

> Any attempt to rigorously define an intuitive concept yields a formal definition that necessarily differs from the original intuition, and the question of correspondence between these two objects arises.

#### 4.3.5 Turning Machines can emulate an abstract RAM

> 内存单元（memory cell）和寄存器（register）是计算机系统中两种不同的存储部件，它们的主要区别如下：

位置和作用
- **内存单元（memory cell）**  
	- 位于主存（RAM）中，是计算机用来长期或临时存储大量数据的地方。  
	- 数量非常多（理论模型中可以是无限多个），访问速度相对较慢。  
	- 用于存放程序数据、变量、数组等。

- **寄存器（register）**  
  - 位于CPU内部，是处理器用来临时存储和操作数据的高速存储单元。  
  - 数量很少（通常几十个以内），但访问速度极快。  
  - 用于存放正在运算的数据、中间结果、地址、程序计数器等。

访问速度
- **内存单元**：访问速度慢（相对于寄存器），但容量大。
- **寄存器**：访问速度极快，但容量极小。
用途
- **内存单元**：主要用于存储大量数据和程序代码。
- **寄存器**：主要用于CPU内部的临时计算、数据交换和控制（如程序计数器、指令寄存器等）。
数量

- **内存单元**：成千上万，甚至理论上无限。
- **寄存器**：极少，通常只有十几个到几十个。

例子
- **内存单元**：RAM中的每一个地址都对应一个内存单元。
- **寄存器**：通用寄存器（如AX、BX）、程序计数器（PC）、堆栈指针（SP）等。


**总结：**  
寄存器是CPU内部的“高速缓存”，数量少但速度快；内存单元是主存中的“普通存储”，数量多但速度慢。寄存器主要用于CPU内部的临时操作，内存单元主要用于存储大量数据和程序。

#### 4.3.6 Uncomputable Functions


> We stress that the theorem holds for any reasonable model of computation. In fact, it only relies on the postulate that each machine in the model has a finite description (i.e., can be described by a string)

这里的 **finite description（有限描述）** 指的是：  
每一台计算模型中的“机器”都可以用**有限长度的信息**（比如一个有限长度的字符串）来完整地描述。

详细解释

- **“有限描述”**意味着：  
	- 你可以用一个有限的、具体的方式，把这台机器的所有结构和行为都写下来。
	- 例如：图灵机的状态集合、符号表、转移函数、初始状态、终止状态等，都可以用有限个符号（比如二进制字符串）来编码。
	- 换句话说，这台机器的“程序”不是无限长的，而是可以被写成一个有限的说明书。

- **为什么强调这一点？**  
	- 这是理论计算机科学中“可计算性”讨论的基础。  
	- 如果机器的描述是无限的，那它本身就无法被实现或模拟，也就失去了讨论“可计算”的意义。

- **举例：**
  - 一台图灵机可以用一张有限的“转移表”来描述。
  - 一个RAM程序可以用有限条指令来描述。
  - 一个有限自动机可以用有限个状态和转移规则来描述。
总结

**finite description** 就是指：  
每台机器都能用有限长度的字符串（或有限的信息）完全描述其结构和行为。  
这保证了模型的“可实现性”和“可讨论性”，是所有“合理计算模型”的基本要求

**Proof**
Since each computable function is computable by a machine that has a finite description, there is a 1–1 correspondence between the set of computable functions and the set of strings (which in turn is in 1–1 correspondence to the natural numbers). On the other hand, there is a 1–1 correspondence between the set of Boolean functions (i.e., functions from strings to a single bit) and the set of real number in $[0, 1)$. This correspondence associates each real r ∈ $[0, 1)$ to the function $f : N → \{0, 1\}$ such that $f (i)$ is the $i^{th}$ bit in the infinite binary expansion of r.

这段证明的核心思想是：**可计算函数的数量是可数的，而所有布尔函数的数量是不可数的**。下面分步解释：

1. 可计算函数和有限描述

- 每一个可计算函数都可以被某台具有**有限描述**的机器计算出来。
- 所有“有限描述”的机器可以用有限长度的字符串来编码（比如写成二进制代码）。
- 所以，“所有可计算函数”与“所有有限字符串”之间是一一对应的关系。
- 而所有有限字符串的集合可以和自然数集合一一对应（因为每个字符串都可以看作一个自然数的二进制表示）。
- **结论：可计算函数的集合是可数的。**

2. 所有布尔函数和实数

- 所有布尔函数（即从字符串到{0,1}的函数）的集合，可以和 $[0,1]$ 区间内的实数一一对应。
- 具体做法：每个 $[0,1]$ 区间内的实数 $r$，都可以写成一个无限二进制小数 $0.b_1b_2b_3\ldots$。
- 于是可以把 $r$ 和一个函数 $f:\mathbb{N}\to\{0,1\}$ 对应起来，$f(i)$ 就是 $r$ 的第 $i$ 个二进制位。
- 这样，每个实数 $r$ 唯一对应一个布尔函数 $f$。
- **结论：所有布尔函数的集合和 $[0,1]$ 区间的实数一样，是不可数的。**

证明的意义

- 可计算函数的数量远远少于所有可能的布尔函数（即所有可能的“从字符串到比特”的函数）。
- 换句话说，**绝大多数布尔函数都是不可计算的**，因为它们无法用有限描述的机器来实现。

总结

- 可计算函数 $\longleftrightarrow$ 有限字符串 $\longleftrightarrow$ 自然数（可数）
- 所有布尔函数 $\longleftrightarrow$ $[0,1]$ 区间的实数（不可数）
- 所以，可计算函数只是所有函数中的极小一部分。

**简要理解：**  
这个证明用集合大小的对比，说明了“可计算函数”只是所有可能函数中的极少数，因为只有有限描述的机器才能实现它们，而大多数函数根本无法被有限描述。

#### 4.3.7 Halting problem

> In contrast to the discussion in §1.2.3.1, at this point we also consider machines that may not halt on some inputs. (The functions computed by such machines are partial functions that are defined only on inputs on which the machine halts.) Again, we rely on the postulate that each machine in the model has a finite description, and denote the description of machine M by \<M\> ∈ {0, 1}∗. The halting function, h : {0, 1}∗× {0, 1}∗→ {0, 1}, is defined such that h(?M?, x)def = 1 if and only if M halts on input x. The following result goes beyond Theorem 1.4 by pointing to an explicit function (of natural interest) that is not computable.

这段话的核心内容是：

1. **与前文的对比**  
   之前（§1.2.3.1）讨论的都是“保证停机”的机器（即对所有输入都会停机的图灵机），现在则**也考虑那些在某些输入上可能不会停机的机器**。

2. **部分函数** : 函数部分有定义
   这样的机器计算出来的函数叫做**部分函数**（partial function）：  
   - 只在机器会停机的输入上有定义（即有输出）。
   - 对于那些机器不会停机的输入，函数没有定义（没有输出）。

3. **有限描述**  
   依然假设每台机器都可以用有限长度的字符串来描述（finite description），比如用二进制字符串编码。用 $<M>$ 表示机器 $M$ 的描述，$<M> \in \{0,1\}^*$。

4. **停机函数的定义**  
   定义了一个**停机函数** $h$：  
   $$
   h : \{0, 1\}^* \times \{0, 1\}^* \to \{0, 1\}
   $$
   其中 $h(?M?, x) = 1$ 当且仅当机器 $M$ 在输入 $x$ 上会停机。

5. **停机问题不可计算**  
   下面要讲的结论比定理1.4更进一步：**它指出了一个非常自然且具体的函数（即停机函数）是不可计算的**。也就是说，没有任何图灵机能够判断任意机器 $M$ 在任意输入 $x$ 上是否会停机。

简要理解

- 现在不仅考虑“总是停机”的机器，也考虑“可能不停机”的机器。
- 这类机器计算的是部分函数（有些输入没结果）。
- 每台机器都能用有限字符串描述。
- 停机函数 $h$ 判断“某台机器在某个输入上是否会停机”。
- 这个函数（停机问题）是不可计算的——没有算法能解决所有情况。

总结

这段话引入了“部分函数”和“停机函数”的概念，并指出停机函数是一个**明确且自然的不可计算函数**，为后续不可判定性理论做铺垫。




我们将证明，即使把停机函数 $h$ 限制在它的“对角线”上（即只考虑 $h(\langle M \rangle, \langle M \rangle)$ 这种形式），得到的函数 $d(\langle M \rangle) \stackrel{\text{def}}{=} h(\langle M \rangle, \langle M \rangle)$，**也是不可计算的**。

详细解释

- **停机函数 $h(\langle M \rangle, x)$**：判断“图灵机 $M$ 在输入 $x$ 上是否会停机”。
- **对角线限制**：只考虑输入和机器编码相同的情况，也就是让机器 $M$ 的输入就是它自己的编码 $\langle M \rangle$。
- **定义 $d(\langle M \rangle) = h(\langle M \rangle, \langle M \rangle)$**：$d$ 是一个新函数，输入是某台机器的编码，输出是“这台机器在自己的编码作为输入时会不会停机”。

这句话的意义

- 停机问题本身已经是不可计算的。
- 现在，即使只考虑“每台机器在自己的描述作为输入时是否停机”这个极其特殊的子问题（对角线），这个问题依然是不可计算的。
- 这说明不可计算性不仅仅是因为输入的多样性，而是问题本身的本质属性。

总结

**即使只问“某台图灵机在自己的编码作为输入时会不会停机”，这个问题也是不可计算的。**  
这进一步加强了停机问题不可判定性的结论。

**Proof:** We will show that even the restriction of $h$ to its “diagonal” (i.e., the function $d(\langle M \rangle) \stackrel{\text{def}}{=} h(\langle M \rangle, \langle M \rangle)$) is not computable. Note that the value of $d(\langle M \rangle)$ refers to the question of what happens when we feed $M$ with its own description, which is indeed a “nasty” (but legitimate) thing to do. We will actually do something “worse”: toward the contradiction, we will consider the value of $d$ when evaluated at a (machine that is related to a) hypothetical machine that supposedly computes $d$.

We start by considering a related function, $d'$, and showing that this function is uncomputable. The function $d'$ is defined on purpose so as to foil any attempt to compute it; that is, for every machine $M$, the value $d'(\langle M \rangle)$ is defined to differ from $M(\langle M \rangle)$. Specifically, the function $d' : \{0, 1\}^* \to \{0, 1\}$ is defined such that $d'(\langle M \rangle) \stackrel{\text{def}}{=} 1$ if and only if $M$ halts on input $\langle M \rangle$ with output $0$. (That is, $d'(\langle M \rangle) = 0$ if either $M$ does not halt on input $\langle M \rangle$ or its output does not equal the value $0$.) Now, suppose, toward the contradiction, that $d'$ is computable by some machine, denoted $M_{d'}$. Note that machine $M_{d'}$ is supposed to halt on every input, and so $M_{d'}$ halts on input $\langle M_{d'} \rangle$. But, by definition of $d'$, it holds that $d'(\langle M_{d'} \rangle) = 1$ if and only if $M_{d'}$ halts on input $\langle M_{d'} \rangle$ with output $0$ (i.e., if and only if $M_{d'}(\langle M_{d'} \rangle) = 0$). Thus, $M_{d'}(\langle M_{d'} \rangle) \neq d'(\langle M_{d'} \rangle)$ in contradiction to the hypothesis that $M_{d'}$ computes $d'$.

We next prove that $d$ is uncomputable, and thus $h$ is uncomputable (because $d(z) = h(z, z)$ for every $z$). To prove that $d$ is uncomputable, we show that if $d$ is computable then so is $d'$ (which we already know not to be the case). Indeed, suppose toward the contradiction that $A$ is an algorithm for computing $d$ (i.e., $A(\langle M \rangle) = d(\langle M \rangle)$ for every machine $M$). Then we construct an algorithm for computing $d'$, which given $\langle M' \rangle$, invokes $A$ on $\langle M'' \rangle$, where $M''$ is defined to operate as follows:

1. On input $x$, machine $M''$ emulates $M'$ on input $x$.
2. If $M'$ halts on input $x$ with output $0$ then $M''$ halts.
3. If $M'$ halts on input $x$ with output different from $0$ then $M''$ enters an infinite loop (and thus does not halt).
4. Otherwise (i.e., $M'$ does not halt on input $x$), then machine $M''$ does not halt (because it just stays stuck in Step 1 forever).

Note that the mapping from $\langle M' \rangle$ to $\langle M'' \rangle$ is easily computable (by augmenting $M'$ with instructions to test its output and enter an infinite loop if necessary), and that $d(\langle M'' \rangle) = d'(\langle M' \rangle)$, because $M''$ halts on $x$ if and only if $M'$ halts on $x$ with output $0$. We thus derived an algorithm for computing $d'$ (i.e., transform the input $\langle M' \rangle$ into $\langle M'' \rangle$ and output $A(\langle M'' \rangle))$, which contradicts the already established fact by which $d'$ is uncomputable. $\blacksquare$

**证明：** 我们将证明，即使将停机函数 $h$ 限制在它的“对角线”上（即函数 $d(\langle M \rangle) \stackrel{\text{def}}{=} h(\langle M \rangle, \langle M \rangle)$），该函数也是不可计算的。注意，$d(\langle M \rangle)$ 的值表示的是当我们将机器 $M$ 的自身描述作为输入时会发生什么，这确实是一个“棘手的”（但合法的）操作。实际上，我们将做更“糟糕”的事情：为了达到矛盾，我们将考虑在一个假设存在的、能够计算 $d$ 的机器（或与之相关的机器）上评估 $d$ 的值。

我们首先考虑一个相关函数 $d'$，并证明该函数不可计算。函数 $d'$ 是故意定义来阻止任何计算尝试的；也就是说，对于每台机器 $M$，$d'(\langle M \rangle)$ 的值被定义为与 $M(\langle M \rangle)$ 不同。具体地，函数 $d' : \{0, 1\}^* \to \{0, 1\}$ 被定义为：当且仅当机器 $M$ 在输入 $\langle M \rangle$ 上停机且输出为 $0$ 时，$d'(\langle M \rangle) \stackrel{\text{def}}{=} 1$。

（也就是说，如果机器 $M$ 在输入 $\langle M \rangle$ 上不停止，或者输出不等于 $0$，则 $d'(\langle M \rangle) = 0$。）现在，假设为了达到矛盾，存在某台机器 $M_{d'}$ 能够计算 $d'$。

注意，机器 $M_{d'}$ 应该在每个输入上都停机 #todo ，因此它在输入 $\langle M_{d'} \rangle$ 上也停机。

#todo 但根据 $d'$ 的定义，$d'(\langle M_{d'} \rangle) = 1$ 当且仅当 $M_{d'}$ 在输入 $\langle M_{d'} \rangle$ 上停机且输出为 $0$（即 $M_{d'}(\langle M_{d'} \rangle) = 0$）。因此，$M_{d'}(\langle M_{d'} \rangle) \neq d'(\langle M_{d'} \rangle)$，这与假设 $M_{d'}$ 计算 $d'$ 矛盾。

> $M(\langle M \rangle)$ 表示的是：
> - **机器 $M$ 在输入 $\langle M \rangle$ 上的输出**。

#todo 
接下来我们证明 $d$ 是不可计算的，因此 $h$ 也是不可计算的（因为对任意 $z$，有 $d(z) = h(z, z)$）。为了证明 $d$ 不可计算，我们展示如果 $d$ 可计算，则 $d'$ 也可计算（而我们已知 $d'$ 不可计算）。确实，假设为了矛盾，存在算法 $A$ 用于计算 $d$（即对每台机器 $M$，$A(\langle M \rangle) = d(\langle M \rangle)$）。那么我们构造一个计算 $d'$ 的算法，给定输入 $\langle M' \rangle$，调用 $A$ 在 $\langle M'' \rangle$ 上，其中机器 $M''$ 定义如下：

1. 对输入 $x$，机器 $M''$ 模拟机器 $M'$ 在输入 $x$ 上的运行。
2. 如果 $M'$ 在输入 $x$ 上停机且输出为 $0$，则 $M''$ 停机。
3. 如果 $M'$ 在输入 $x$ 上停机且输出不为 $0$，则 $M''$ 进入无限循环（因此不停止）。
4. 否则（即 $M'$ 在输入 $x$ 上不停止），机器 $M''$ 也不停止（因为它在步骤1中一直卡住）。

注意，从 $\langle M' \rangle$ 到 $\langle M'' \rangle$ 的映射是容易计算的（通过在 $M'$ 上增加测试输出并在必要时进入无限循环的指令实现），且 $d(\langle M'' \rangle) = d'(\langle M' \rangle)$，因为 $M''$ 在输入 $x$ 上停机当且仅当 $M'$ 在输入 $x$ 上停机且输出为 $0$。因此，我们得到了一个计算 $d'$ 的算法（即将输入 $\langle M' \rangle$ 转换为 $\langle M'' \rangle$ 并输出 $A(\langle M'' \rangle)$），这与已知的 $d'$ 不可计算的事实矛盾。$\blacksquare$


### 4.4 Turing-reductions

**Turing-reductions（图灵归约）**是理论计算机科学中用来比较问题复杂性和可计算性的一种重要工具。它描述了一种通过调用另一个问题的“黑盒子”来解决当前问题的方法。

1. 基本概念

- **归约（Reduction）**：将一个问题转化为另一个问题，从而利用后者的解法来解决前者。
- **图灵归约**：允许在求解一个问题时，多次调用另一个问题的解答（oracle），并根据调用结果动态决定下一步操作。

2. 形式定义

假设有两个决策问题 $A$ 和 $B$：

- $A$ **图灵归约**到 $B$（记作 $A \leq_T B$），意味着存在一个图灵机 $M$，它可以访问一个“求解 $B$ 的黑盒子”（oracle），通过有限次调用这个黑盒子，$M$ 能够决定 $A$ 的任意实例。

换句话说，解决 $A$ 的问题可以通过调用解决 $B$ 的方法来完成。

3. 特点

- **灵活性强**：图灵归约允许多次调用 oracle，调用顺序和次数可以根据之前的结果动态调整。
- **比其他归约更强**：比如，许多其他归约（如Karp归约）只允许一次调用或有限次调用，图灵归约更为宽松。

4. 应用

- 用于证明某些问题的不可计算性或复杂性。
- 通过图灵归约，可以将一个复杂问题归约到另一个已知难解的问题，说明前者至少和后者一样难。
- 在可计算性理论中，图灵归约帮助定义了可计算性等级和不可判定问题的分类。

5. 简单比喻

想象你有一个万能的“问题求解器”（oracle），它能瞬间解决问题 $B$。图灵归约允许你在解决问题 $A$ 时，多次向这个求解器提问，并根据答案调整策略，最终解决 $A$。

**总结：**  
图灵归约是一种强大的归约方式，允许通过多次调用另一个问题的解法（oracle）来解决当前问题，是研究问题间计算关系和复杂度的重要工具。

### 4.5 Rice’s Theorem

> Every nontrivial decision problem regarding the function computed by a given Turing machine has no algorithmic solution.

- the function computed by a given Turing machine: Also called the partial function defined by a Turing machine

**Rice 定理（Rice’s Theorem）**是计算理论中的一个重要结果，它揭示了关于图灵机所计算函数性质的判定问题的普遍不可判定性。

定理内容

**Rice 定理指出：**  
对于任何**非平凡的**性质（nontrivial property）——即既不是所有图灵机都满足，也不是所有图灵机都不满足的性质——关于图灵机所计算函数的判定问题是**不可算法解决的**。

换句话说，任何试图判断一个图灵机计算的函数是否具有某种非平凡性质的问题，都不存在通用的算法来解决。

详细解释

- **判定问题**：给定一台图灵机，判断它计算的函数是否满足某个特定性质（比如“函数是否恒等于零”、“函数是否总是有定义”、“函数是否是恒等函数”等）。
- **非平凡性质**：性质既不是对所有图灵机都成立，也不是对所有图灵机都不成立。换句话说，这个性质在某些图灵机上成立，在另一些图灵机上不成立。
- **不可算法解决**：不存在一个算法能对所有图灵机的描述正确判断该性质是否成立。

例子

- 判断图灵机计算的函数是否是恒等函数。
- 判断图灵机计算的函数是否总是有定义（即是否是全函数）。
- 判断图灵机计算的函数是否在某个输入上有特定输出。

这些问题都是 Rice 定理所涵盖的非平凡性质，因而都是不可判定的。

意义

Rice 定理表明，**关于图灵机计算函数的任何非平凡性质的判定问题都是不可判定的**，这极大地限制了我们能自动分析程序行为的能力。

简要总结

**Rice 定理**告诉我们：  
任何非平凡的关于图灵机计算函数的性质，都没有通用算法可以判定。这是计算不可判定性理论中的一个核心结论。

> Theorem 1.6 means that no algorithm can determine any nontrivial property of the function computed by a given computer program (written in any programming language). For example, no algorithm can determine whether or not a given computer program halts on each possible input. The relevance of this assertion to the project of program verification is obvious.

这句话的意思是：

**Rice 定理表明，没有任何算法能够判定一个给定计算机程序（无论用什么编程语言编写）所计算函数的任何非平凡性质。**

详细理解

- **非平凡性质（nontrivial property）**：指的是既不是所有程序都满足，也不是所有程序都不满足的性质。比如“程序是否总是停机”就是一个非平凡性质，因为有些程序会停机，有些不会。
- **无法判定**：不存在一个通用算法，能够对任意程序判断它是否具有某个非平凡性质。
- **举例说明**：没有算法能判断一个程序是否对所有可能的输入都会停机（即“停机问题”不可判定）。
- **对程序验证的影响**：这说明自动化程序验证（比如自动证明程序正确性、检测程序是否有死循环等）存在根本的限制，不能完全依赖算法来解决所有问题。

简要总结

Rice 定理告诉我们，**程序的很多重要性质是不可自动判定的**，这对程序验证领域提出了根本性的挑战和限制。


### 4.6 The Post Correspondence Problem

**邮政对应问题（Post Correspondence Problem，简称 PCP）**是一个经典的不可判定问题。问题的输入由两组字符串序列组成，分别是  
$$(\alpha_1, \alpha_2, \ldots, \alpha_k) \quad \text{和} \quad (\beta_1, \beta_2, \ldots, \beta_k)$$  
问题是：是否存在一个索引序列  
$$i_1, i_2, \ldots, i_\ell \in \{1, 2, \ldots, k\}$$  
使得将对应的字符串按该序列连接后，两组字符串相等：  
$$\alpha_{i_1} \alpha_{i_2} \cdots \alpha_{i_\ell} = \beta_{i_1} \beta_{i_2} \cdots \beta_{i_\ell}$$  
其中，序列的长度 $\ell$ 没有事先限制，可以是任意长。

介绍  
邮政对应问题是计算理论中的一个重要问题，它展示了在计算机科学中存在一些根本无法通过算法解决的问题。具体来说：

- 给定两组字符串序列，问题是判断是否存在一种方式，通过选择索引序列，使得两组字符串连接后完全相同。
- 这个问题的难点在于，索引序列的长度没有上限，可能非常长，导致无法通过有限步骤的算法穷举所有可能。
- **邮政对应问题是不可判定的**，也就是说不存在一个通用算法能对所有输入判断是否存在这样的索引序列。
- 该问题的不可判定性通常通过归约已知的不可判定问题（如停机问题）来证明。

邮政对应问题不仅是理论计算机科学中的经典例子，也在形式语言、自动机理论等领域有重要应用，体现了计算不可判定性的本质。

#### 4.6.1 例子陈述

假设有两组字符串序列：

$$
\alpha = (\text{a}, \text{ab}, \text{bba})
$$

$$
\beta = (\text{baa}, \text{a}, \text{bb})
$$

问题是：是否存在一个索引序列 $i_1, i_2, \ldots, i_\ell$，使得

$$
\alpha_{i_1} \alpha_{i_2} \cdots \alpha_{i_\ell} = \beta_{i_1} \beta_{i_2} \cdots \beta_{i_\ell}
$$


#### 4.6.2 例子解析

- 试试索引序列 $(2, 3, 1)$：
$$
\alpha_2 \alpha_3 \alpha_1 = \text{ab} \cdot \text{bba} \cdot \text{a} = \text{abbbaa}
$$
$$
\beta_2 \beta_3 \beta_1 = \text{a} \cdot \text{bb} \cdot \text{baa} = \text{abbbaa}
$$

两边字符串相等，说明存在这样的索引序列。

#### 4.6.3 结论

这个例子说明，邮政对应问题就是寻找这样一个索引序列，使得两组字符串按该序列连接后相等。虽然在这个简单例子中找到了答案，但一般情况下，判断是否存在这样的序列是不可判定的。

## 5 Universal Algorithm

**Universal Algorithm（通用算法）**是指一种能够模拟任何其他算法或计算过程的算法。它的核心特点是：

 定义

- 通用算法可以接受**任意算法的描述**（通常以某种编码形式表示）和该算法的输入，然后模拟该算法在该输入上的运行过程。
- 换句话说，通用算法是一个“算法的算法”，能够执行任何给定的算法。

 典型例子

- **图灵机中的通用图灵机（Universal Turing Machine）**：  
  它能读取任意图灵机的编码和输入，模拟该图灵机的计算过程。
- **现代计算机中的解释器或虚拟机**：  
  例如，Java虚拟机（JVM）可以执行任何用Java编写的程序；Python解释器可以执行任何Python代码。

作用和意义

- 通用算法体现了“计算的普适性”，说明所有可计算的问题都可以由一个统一的机器或算法来处理。
- 它是计算理论的基石，支持了现代计算机的设计理念——一台机器通过不同的软件可以完成各种任务。

简单理解

通用算法就像一个“万能的机器”，只要给它任何算法和输入，它都能模拟执行那个算法，得到相应的输出。

---

**总结：**  
通用算法是能够模拟任何其他算法的算法，是计算理论中描述“通用计算能力”的核心概念。

### 5.1 Kolmogorov Complexity

**Kolmogorov Complexity（柯尔莫哥洛夫复杂度）**是信息理论和算法理论中的一个重要概念，用来衡量一个字符串的“信息量”或“复杂度”。

定义

- 某个字符串的柯尔莫哥洛夫复杂度，指的是**生成该字符串的最短程序的长度**（通常以二进制长度计）。
- 这里的“程序”是指在某个固定的通用计算模型（如通用图灵机）上运行的程序。
- 简单来说，就是描述该字符串所需的最简明指令数。

直观理解

- 如果一个字符串非常有规律，比如“1111111111”，它可以用一个很短的程序描述（比如“打印10个1”）。
- 如果一个字符串完全随机，没有任何规律，那么描述它的最短程序可能就是直接输出它本身，程序长度接近字符串长度。
- 因此，柯尔莫哥洛夫复杂度反映了字符串的“压缩难度”或“随机性”。

形式表达

设 $U$ 是一个固定的通用图灵机，字符串 $x$ 的柯尔莫哥洛夫复杂度定义为：

$$
K_U(x) = \min \{ |p| : U(p) = x \}
$$

其中，$p$ 是输入给 $U$ 的程序，$|p|$ 是程序的长度，$U(p) = x$ 表示 $U$ 运行程序 $p$ 输出字符串 $x$。

重要性质

- **不可计算性**：柯尔莫哥洛夫复杂度是不可计算的，无法设计算法准确计算任意字符串的复杂度。
- **依赖于选择的通用机**：不同的通用图灵机定义的复杂度可能不同，但差异是一个常数，与字符串长度无关。
- **与压缩相关**：柯尔莫哥洛夫复杂度是理论上的最优压缩长度。

应用

- 理论计算机科学中的随机性定义。
- 信息论中的数据压缩极限。
- 复杂系统和人工智能中的模式识别。


**总结：**  
柯尔莫哥洛夫复杂度衡量一个字符串最简洁的描述长度，是理解信息和随机性的基础工具。

绕道讲一下：**柯尔莫哥洛夫复杂度**。通用机器的存在，可以看作是用来书写对象的有效且简洁描述的通用语言，这在柯尔莫哥洛夫复杂度中起着核心作用。粗略地说，柯尔莫哥洛夫复杂度关注的是对象的（有效）描述的长度，并将这种最短长度视为该对象固有的“复杂度”；也就是说，“简单”的对象（或现象）是那些具有简短描述（或简短解释）的对象，而“复杂”的对象则没有简短的描述。毋庸置疑，这些（有效的）描述必须依赖于某个固定的“语言”（即某个固定的机器，该机器给出对象的简洁描述后，能够生成其明确的描述）。

w

#theorem 
Theorem 1.10 (complexity wrt a universal machine):  
Let $U$ be a [[universal machine]]. Then, for every machine $M'$, there exists a constant $c$ such that  
$$K_U(s) \leq K_{M'}(s) + c$$  
for every string $s$.
## 6 Time and Space Complexity