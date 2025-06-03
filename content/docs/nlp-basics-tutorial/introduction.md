---
title: "第一章：NLP 简介与文本预处理"
linkTitle: "1. 简介与文本预处理"
weight: 10 # 在 "NLP 基础教程" 这个子菜单中，这是第一项
parent: "NLP 基础教程"
description: "了解 NLP 的基本概念，并学习文本数据在进行分析前常用的预处理步骤。"
---

## 1.1 什么是自然语言处理 (NLP)?

自然语言处理 (Natural Language Processing, NLP) 是计算机科学、人工智能和语言学交叉领域的一个分支。它关注的是计算机与人类（自然）语言之间的交互，特别是如何编程计算机以处理和分析大量的自然语言数据。

NLP 的目标是让计算机能够“理解”人类语言的内容，包括上下文、情感以及语言的细微差别。

**NLP 的应用场景非常广泛，例如：**
*   **机器翻译**: Google Translate, DeepL
*   **情感分析**: 分析用户评论的情感倾向
*   **垃圾邮件检测**
*   **聊天机器人与虚拟助手**: Siri, Alexa, ChatGPT
*   **文本摘要**
*   **信息提取与问答系统**

## 1.2 文本预处理

原始的文本数据通常是“脏”的，包含许多对分析无用甚至有害的信息。因此，在进行 NLP 任务之前，文本预处理是一个至关重要的步骤。

常见的文本预处理技术包括：

### 1.2.1 分词 (Tokenization)
将文本分割成有意义的单元，称为词元 (tokens)。词元通常是单词，但也可能是标点符号或数字。

例如，句子 "NLP is fascinating!" 可以被分词为：`["NLP", "is", "fascinating", "!"]`

### 1.2.2 转换为小写 (Lowercasing)
将所有文本转换为小写，以确保对相同单词的不同大小写形式（如 "Apple" 和 "apple"）进行统一处理。

### 1.2.3 去除标点符号
根据任务需求，标点符号有时需要被移除。

### 1.2.4 去除停用词 (Stop Word Removal)
停用词是语言中非常常见但通常不携带太多实际意义的词，如 "is", "a", "the", "in" 等。移除停用词可以减少数据维度并突出重要词汇。

### 1.2.5 词形还原 (Lemmatization) 与 词干提取 (Stemming)
*   **词干提取 (Stemming)**: 将单词简化为其词干或基本形式。例如，"running", "ran", "runner" 可能都被简化为 "run"。词干提取速度快，但有时结果可能不是一个真实的单词。
*   **词形还原 (Lemmatization)**: 将单词转换为其词典中的基本形式（词元，lemma）。例如，"better" 会被转换为 "good"。词形还原通常更准确，但需要词典支持，速度相对较慢。

**示例 (使用 Python NLTK 库):**
```python
import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import stopwords
from nltk.stem import PorterStemmer, WordNetLemmatizer

# 你可能需要先下载 NLTK 资源 (如果之前没有下载过)
# nltk.download('punkt', quiet=True)
# nltk.download('stopwords', quiet=True)
# nltk.download('wordnet', quiet=True)
# nltk.download('omw-1.4', quiet=True) # wordnet 需要 omw-1.4

text = "Natural Language Processing is really fascinating and offers many opportunities!"
text_lower = text.lower()
tokens = word_tokenize(text_lower)

stop_words = set(stopwords.words('english'))
# 确保单词是字母数字组合 (isalnum) 并且不在停用词列表中
filtered_tokens = [word for word in tokens if word.isalnum() and word not in stop_words]

stemmer = PorterStemmer()
stemmed_tokens = [stemmer.stem(word) for word in filtered_tokens]

lemmatizer = WordNetLemmatizer()
lemmatized_tokens = [lemmatizer.lemmatize(word) for word in filtered_tokens]

print("Original Tokens:", tokens)
print("Filtered Tokens:", filtered_tokens)
print("Stemmed Tokens:", stemmed_tokens)
print("Lemmatized Tokens:", lemmatized_tokens)
```

## 总结
本章介绍了 NLP 的基本概念及其广泛的应用，并详细讨论了文本预处理的常用技术。有效的文本预处理是成功执行后续 NLP 任务的关键。下一章我们将探讨如何将文本数据转换为机器可以理解的数字表示。
