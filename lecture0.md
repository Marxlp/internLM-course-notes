Lecture 0

## 序言

 神经网络模型目前整体处在从独立领域模型走向通用大模型。

## InternLM 开源体系整体概览

   * 书生浦语模型从 23 年中开始发布。

   * 三个量级参数的大模型: 7B, 20B, 123B

   * InternLM 包含了 `书生.万卷`, `InternLM-train`, `XTunner`, `LMDeploy`, `OpenCompass`, `Lagent/AgentLego` 等从数据到训练到部署的全链路工具

## 从模型到应用--决定怎么使用模型

   * step1 看业务场景是否复杂, 如果“否” 则到step4 使用大模型进行评测, 如果“是” 到step2
  
   * step2 算力是否足够，如果是则微调，如果否则部分参数微调
 
   * step3 是否需要和环境交互，如果是则建智能体, 否则进行 step4 大模型评测

   * step4 进行模型评测

## 数据-书生.万卷 1.0 (openDataLab)
  
   * 30+ 模态
    
   * 文本：包含 50 亿个文档, 数据量超 1TB

   * 图像文本对数据集: 2,200万个文件，140GB 数据

   * 视频数据: 1000 个文件，900GB

## InterLM-train
   
   * 高可扩展: 支持千卡

   * 极致性能优化: Hybrid Zero 技术，在512 张卡上，比Megatron-deepspeed 快一倍

   * 兼容主流

   * 开箱即用

## XTunner 高效微调

   * 支持增量、指令微调
 
   * 兼容 LLama, Qwen, BaiChuan, ChatGLM

   * 最低只要 8GB 即可微调

## OpenCompass 测评

   * 分为六大维度：学科、语言、知识、理解、推理、安全

   * 支持主客观, 自动化客观评测，基于模型辅助的主观评测，基于人类反馈的主观评测

   * 分布式、丰富模型支持

## LMDeploy 部署

   * 难点：

        - 内存开销大: 庞大参数量; 采用自回归生成的token, 需要缓存k/v

        - 动态shape: 请求参数不固定；token 逐个生成，数量不定

        - 模型结构简单: 大部分为decoder-only

   * 技术点:
      
        - 模型并行

        - 低比特量化

        - Attention 优化

        - 计算和访存优化

        - continous batching

   * 接口方案:
        
        - Python

        - gRPC

        - RESTful

## Lagent/AgentLego

   * 大语言模型的局限性

        - 最新信息和知识的获取

        - 回复的可靠性

        - 数学计算

        - 工具使用和交互

   * Lagent 支持多种类型

        - ReAct

        - Rewoo

        - AutoGPT

   * AgentLego 多模态智能体工具

        - 前沿算法

        - 支持调用 LangChain, Lagent, Transformer Agents

