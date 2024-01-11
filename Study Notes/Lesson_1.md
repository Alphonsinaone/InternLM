# 书生·浦语大模型全链路开源体系
## 背景——大模型成为热门关键词
![image](https://github.com/Alphonsinaone/InternLM/assets/155552157/d0c14aed-96b2-4b36-aaea-196934b191d7)  
原因：大模型是发展通用人工智能的重要途径  
AI的发展历程：专用模型→通用模型  
&ensp;&ensp;&ensp;&ensp;专用模型：针对特定任务，一个模型解决一个问题（过去一二十年，深度学习理论获得突破以来，如人脸识别、AlphaGo等）  
&ensp;&ensp;&ensp;&ensp;通用大模型：一个模型应对多种任务、多种模态（近两年的发展，如ChatGPT）  
## 书生·浦语大模型开源历程  
![image](https://github.com/Alphonsinaone/InternLM/assets/155552157/ed753fee-a41a-42eb-ba9c-87e395cafbb4)  
轻量级→中量级→重量级  
&ensp;&ensp;&ensp;&ensp;轻量级：InternLM7B，70亿参数的模型，方便部署，低成本可用  
&ensp;&ensp;&ensp;&ensp;中量级：InternLM-20B， 能够在模型能力与推理代价间取得较好的平衡，为商用场景提供了可开发定制高精度的较小规模的模型  
&ensp;&ensp;&ensp;&ensp;重量级：InternLM-123B，千亿参数的模型，具备强大的性能  
## 书生·浦语20B开源大模型性能  
以不足三分之一的参数量，达到Llama2-70B的水平  
## 从模型到应用  
典型的大模型应用：智能客服、个人助手、行业应用  
从模型到应用需要一些工具/框架协助完成，以下是一个典型的例子：  
![image](https://github.com/Alphonsinaone/InternLM/assets/155552157/30f0c396-275f-4fe3-881b-ad506fc63e3a)
Step 1. 模型的选型：关注开源模型不同维度上面的能力（针对于应用场景），本质上是一个**模型评测**的过程  
Step 2. 评估业务场景：是否足够的复杂，直接使用模型是否满足需求  
Step 3. 模型的微调：在业务场景较为复杂的情况下，需要判断算力是否足够→  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;若算力足够，进行模型的续训/全参数微调  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;若算力受限，进行部分参数的微调  
Step 4. 是否需要和环境进行交互：例如调用外部的API，或者和已有业务的数据库进行交互  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;若是，转Step 5；若否，转Step 6  
Step 5. 构建基于大模型的智能体：在业务场景中有更好的表现  
Step 6. 模型评测：若评测不通过，则需要重新进行模型的微调或迭代  
Step 7. 模型部署：如何使用更少的资源，如何提升整个应用的吞吐量  
## 书生·浦语全链条开源开放体系  
![image](https://github.com/Alphonsinaone/InternLM/assets/155552157/fcc6bfd9-b49e-4ae8-9e2c-4c9dbe08df22)

**数据——书生·万卷**  
开源的多模态语料库：包括文本数据、图像·文本数据、视频数据  
大小：超过2TB  
多模态融合：范围涵盖科技、文学、媒体、教育等不同的领域  
精细化处理：应用了书生·浦语研发过程中积累的数据预处理/数据清洗的技术  
价值观对齐：把数据的内容和现在主流的价值观进行对齐，更加合法合规，提升语料库的纯净度  
其他开放的数据平台：OpenDataLab  

**预训练——InternLM-Train**  
四大特点：
1. 高可拓展性：支持从8卡到千卡的训练，千卡的加速效率达到92%  
2. 极值的性能优化：Hybrid Zero，独特技术+极致优化，加速50%  
3. 兼容主流：兼容如HuggingFace等技术生态，支持各类轻量化技术  
4. 开箱即用：支持多种规格的语言模型，修改配置即可进行训练  

**微调——XTuner**  
在大语言模型的下游应用中经常用到的两种方式：增量续训和有监督微调  
1. 增量续训  
   使用场景：让基座模型学习到一些新知识，如某个垂类领域知识  
   训练数据：文章、书籍、代码等，训练数据格式和预训练一致  
2. 有监督微调  
   使用场景：让模型学会理解和遵循各种指令，或者注入少量领域知识  
   训练数据：高质量的对话、问答数据，数据量相比于增量续训/预训练较小  

高效微调框架 **XTuner**  
1. 适配多种生态  
   多种微调算法：兼容多种微调策略与算法（如LoRA、QLoRA），覆盖各类SFT场景  
   适配多种开源生态：支持加载HuggingFace、ModelScope模型或数据集  
   自动优化加速：开发者无需关注复杂的显存优化与计算加速细节  
2. 适配多种硬件  
   训练方案覆盖NVIDIA 20系以上所有显卡  
   <u>最低只需8GB显存即可微调7B模型</u>

**评测——OpenCompass**  
国内外评测体系的整体趋势  
![image](https://github.com/Alphonsinaone/InternLM/assets/155552157/447e9197-3107-44e3-9b65-cfc38c2d31d2)
从评测的全面性来说不能满足目前大模型的发展  

开源评测体系 **OpenCompass** （支持6大维度，80+评测集，40万+评测题目）  
![image](https://github.com/Alphonsinaone/InternLM/assets/155552157/b250b152-3ca0-4e99-8f44-2be2aa4e7ad1)
大模型能力6大维度：
1. 学科
2. 语言
3. 知识
4. 理解
5. 推理
6. 安全

OpenCompass开源评测平台架构  
![image](https://github.com/Alphonsinaone/InternLM/assets/155552157/1a23badb-26ad-4dc9-9ec5-e87bc3070cbb)
1. 模型层：支持基座模型和对话模型  
2. 能力层：包括通用能力和特色能力（专门的能力维度）的评测，随着大模型领域的发展不断更新  
3. 方法层：支持自动化客观评测、基于模型辅助的主管评测、基于人类反馈的主观评测  
4. 工具层：提供分布式评测、提示词工程、评测数据库上报、评测榜单发布、评测报告生成  

OpenCompass的亮点  
1. 丰富的模型支持：开源模型，API模型一站式评测  
2. 分布式高效评测：支持千亿参数模型在海量数据集上分布式评测  
3. 便捷的数据集接口：支持社区用户根据自身需求快速添加自定义数据集  
4. 敏捷的能力迭代：每周更新大模型能力榜单，每月提升评测工具能力  

**部署——LMDeploy**  
大语言模型特点  
1. 内存开销巨大  
   庞大的参数量  
   采用自回归生成token，需要缓存k/v  
2. 动态Shape  
   请求数不固定  
   token逐个生成，且数量不固定（根据用户请求）  
3. 模型结构相对简单  
   Transformer结构，大部分是decoder-only  

技术挑战  
1. 设备  
   低存储设备（消费级显卡、移动端等）如何部署？  
2. 推理  
   如何加速token的生成速度  
   如何解决动态shape，让推理可以不间断  
   如何有效管理和利用内存  
3. 服务  
   提升系统整体吞吐量  
   降低请求的平均响应时间  

部署方案  
1. 技术点  
   模型并行  
   低比特量化  
   Attention优化  
   计算和访存优化  
   Continuous Batching（大语言模型特有）  

高效推理框架 **LMDeploy** （提供大模型在GPU上部署的全流程解决方案，包括模型轻量化、推理和服务）  
对外提供的接口：Python、gRPC、RESTful  
轻量化：4bit权重，8bit k/v  
推理引擎：turbomind、pytorch  
服务：openai-server、gradio、triton inference server  
LMDeploy的特点：  
1. 高效推理引擎  
   持续批处理技巧  
   深度优化的低比特计算kernel  
   模型并行  
   高效的k/v缓存管理机制  
2. 完备易用的工具链  
   量化、推理、服务全流程  
   无缝对接OpenCompass评测推理精度  
   和OpenAI接口高度兼容的API server  
3. 领先的推理性能  
   静态推理性能：固定batch，输入/输出token数量  
   动态推理性能：真实对话，不定长的输入/输出  

**应用——智能体**  
大语言模型的局限性：  
1. 最新信息和知识的获取
2. 回复的可靠性
3. 数学计算
4. 工具使用和交互
LLM驱动智能体
![image](https://github.com/Alphonsinaone/InternLM/assets/155552157/a018adfd-5056-4642-bc19-7fd65d140c2f)
智能体以LLM为核心，进行规划、推理、执行等。  

轻量级智能体框架 **Lagent**  
1. 支持多种类型的智能体能力  
   ![image](https://github.com/Alphonsinaone/InternLM/assets/155552157/990b2336-cf8d-4e18-9c54-3d81d3cd11ef)
2. 灵活支持多种大语言模型  
   GPT-3.5/4&ensp;&ensp;&ensp;&ensp;InternLM&ensp;&ensp;&ensp;&ensp;Hugging Face Transformers&ensp;&ensp;&ensp;&ensp;Llama
3. 简单易拓展，支持丰富的工具  
   AI工具：文生图、文生语音、图片描述  
   能力拓展：搜索、计算器、代码解释器
   Rapid API：出行API、财经API、体育资讯API

多模态智能体工具箱 **AgentLego**  
聚焦在给大模型提供更多的工具集合  
1. 丰富的工具集合，尤其是提供了大量视觉、多模态相关领域的前沿算法功能  
2. 支持多个主流智能体系统，如LangChain、Tranformers Agent、Lagent等  
3. 灵活的多模态工具调用接口，可以轻松支持各类输入输出格式的工具函数  
4. 一键式远程工具部署，轻松使用和调试大模型智能体  
