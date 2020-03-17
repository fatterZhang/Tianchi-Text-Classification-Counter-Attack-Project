
## 安全AI挑战者计划第三期 - 文本分类对抗攻击比赛方案
### 比赛链接
https://tianchi.aliyun.com/competition/entrance/231762/introduction
### 方案概述和排名
比赛方案为：字典检测+形似字/音似字/拼音攻击。针对每一条原始样本生成512条攻击候选样本，再选取得分最高的句子作为攻击选项。<br>

最终得分和排名为44 /133.40，参赛人数为1175（rank5%）

### 文件说明
├── README.md                                     | 这篇说明文档<br>
├── benchmark_texts.txt                           | 示例输入文本，用来读取后生成提交结果<br>
├── requirements.txt                              | 在此填写需要的Python依赖包<br>
├── main.py                                       | 镜像中执行的Python脚本<br>
├── sanity_check.py                               | 用于检查生成的提交结果文件的脚本<br>
├── Dockerfile                                    | Docker配置文件<br>
└── run.sh                                        | 执行Python脚本的shell脚本<br>
##### 模型实现
├── lzk_detect_1.py      | 标记原始字符串的脏话。2为必改，1为脏话，0为正常<br>
├── lzk_disturb_2.py	   | 扰动函数，输入标记序列，输出所有可能攻击<br>
├── lzk_calculate_1.py   | 根据所有可能(512条)，计算p最高并返回<br>
├── distance_module      | 比赛方提供的计算[句子相似度模块](https://tianchi.aliyun.com/competition/entrance/231762/information)
├── reference_model      | 比赛方提供的[脏话分类模块](https://tianchi.aliyun.com/competition/entrance/231762/information)
└── preprocessing_module | 比赛方提供的[句子预处理模块](https://tianchi.aliyun.com/competition/entrance/231762/information)
##### 数据
├── small.txt					| 小样本脏话测试<br>
├── data/abuse_dict.json		| 脏话词典<br>
├── data/abuse_dict_yizi.json	| 一个字的脏话词典<br>
└── data/mynewword3.json		| 汉字词典（包含所有字的形似字，音似字，拆字，部首等信息）<br>



