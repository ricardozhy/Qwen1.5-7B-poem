# Qwen1.5-7B-poem: 古诗词领域基座模型

## 简介
Qwen1.5-7B-poem 是一个基于 Qwen1.5-7B 模型，在海量高质量中国古诗词数据上进行继续预训练（Pre-training）而成的领域基座模型。

本项目旨在构建一个深度融合中国古诗词文化知识的语言模型基座，为后续在古诗词生成、赏析、问答、翻译等多种下游任务上的指令微调（Instruction-tuning）提供一个强大而坚实的起点。

## 主要特点
- **深厚领域知识**: 模型通过学习约5.2亿字符的专业语料，对古诗词的语言风格、韵律、作者、朝代背景、注释翻译等建立了深刻的理解。
- **卓越续写能力**: 作为一个基座模型 (Base Model)，它在文本补全和续写方面表现出色，能够自然地承接上文，生成符合韵律和意境的文段。
- **强大的微调潜力**: 是进行指令微调的理想基座。开发者可以利用其丰富的内化知识，通过少量有监督数据微调，即可在特定任务上达到优异性能。
- **开源开放**: 模型、代码和训练细节完全开放，鼓励社区在此基座上进行探索和创新。

## 使用方法

### 环境准备
首先，请确保您已经安装了 transformers、torch 等必要的库。

```bash
pip install transformers
```

### 模型加载
您可以直接从 Hugging Face 或 ModelScope 加载模型。

**Hugging Face:**
```python
from transformers import AutoModelForCausalLM, AutoTokenizer

model_id = "ricardozhy/Qwen1.5-7B-poem"
tokenizer = AutoTokenizer.from_pretrained(model_id, trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained(
    model_id,
    torch_dtype="auto",
    device_map="auto",
    trust_remote_code=True
)
```

**ModelScope:**
```python
from modelscope import AutoModelForCausalLM, AutoTokenizer

model_id = "njauzwh/Qwen1.5-7B-poem"
tokenizer = AutoTokenizer.from_pretrained(model_id, trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained(
    model_id,
    torch_dtype="auto",
    device_map="auto",
    trust_remote_code=True
)
```
## 训练数据
本模型使用的核心训练数据来源于 GitHub 开源项目 [VMIJUNV/chinese-poetry-and-prose](https://github.com/VMIJUNV/chinese-poetry-and-prose)。

- **数据规模**: 语料总计约 5.2亿字符。
- **数据内容**: 覆盖了从先秦到近代的数万名诗人的作品，包含了丰富的元信息，如诗词原文、作者朝代、现代文翻译、字词注释、作品赏析等。

## 应用场景与未来方向
为了将该模型的能力应用于实际场景，我们强烈建议开发者在此模型的基座上进行指令微调 (Instruction-tuning)。通过构建特定任务的指令数据集，您可以将 Qwen1.5-7B-poem 适配到以下各类应用中：

- 古诗词生成: 根据主题、意象、体裁（五言、七言、词牌）等指令创作诗词。
- 智能问答: 建立一个能够回答关于诗人、作品背景、诗句含义等问题的智能系统。
- 自动赏析: 输入一首诗，模型可以自动生成赏析文段。
- 古文翻译: 提升古诗词到现代白话文的翻译质量和流畅度。
- 教育辅助: 开发辅助学生学习和理解古诗词的工具。
- 数字人文研究: 作为强大的工具，辅助进行文学计量学、作者归属等研究。

## 许可证
本项目采用 **Apache License 2.0** 许可证。

## 开源社区与联系方式
如果您觉得这个项目对您有帮助，欢迎在 GitHub 上给我们一个 ⭐️ Star，您的支持是我们持续优化的最大动力！

如有任何问题，欢迎通过 GitHub Issues 提交。
- GitHub Issues: [提交问题](https://github.com/ricardozhy/Qwen1.5-7B-poem/issues)
- 邮箱：zhaowenhua@njau.edu.cn
  
## 致谢
特别感谢 [VMIJUNV/chinese-poetry-and-prose](https://github.com/VMIJUNV/chinese-poetry-and-prose) 项目及其贡献者们整理并提供的宝贵数据集，为本项目提供了坚实的数据基座。
