# 以几个常见的开源模型出发，看看LLM跑的benchmark的情况

## 目的

我们经常看到介绍某个模型在某某榜单上排名超过了“谁谁谁”，然后怀着期待的心情，下载好几十G或者上百G，一部署往往发现效果不太行，发出“就这”的感叹。因此我就想研究一下大模型评测榜单这块，看看到底哪些榜单有价值，以后着重看那些有价值的榜单，那些比较水的榜单以后就不看了。

## 模型

- [https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B)
- [https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash)
- [https://huggingface.co/tencent/Hy4-preview](https://huggingface.co/tencent/Hy4-preview)
- [https://huggingface.co/moonshotai/Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3)
- https://huggingface.co/zai-org/GLM-5.3
- https://huggingface.co/ornith-ai/Ornith-1.5-397B
- https://huggingface.co/Qwen/Qwen3.8-Flash-Next
- GPT-6 Astra
- Fable 5
- 其他的旗舰模型

## 输出格式

- 输出stat.md
- 表格包含的列：benchmark, 类型, 简介, 跑分的模型数, 表现最好的模型, 备注
- 按照值得参考的程度进行排序

