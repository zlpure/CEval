# C-Eval + ChatGLM2-6B
本项目旨在使用开源的[ChatGLM2-6B](https://github.com/THUDM/ChatGLM2-6B/tree/main)模型，在中文评测框架[C-Evaluation](https://cevalbenchmark.com/)上进行效果评测。

C-Eval各个模型总的评测结果请参考[LeaderBoard](https://cevalbenchmark.com/static/leaderboard.html)，测试样例请参看[探索样例](https://cevalbenchmark.com/static/explore.html)。ChatGLM2-6B官方Github评测结果的Average Score是50.1，ChatGLM2-6B在C-Eval上提交的结果是51.7，本项目的结果是50.7，评测结果基本一致。具体结果列表如下：

|  Model  | Average  | STEM | Social  Sciences | Humanities |  Others |  
|  ----  | ----  | ----  |----  |----  |----  |
| ChatGLM2-6B-Github  | 50.1 | 46.4 | 60.4 | 50.6 | 46.9 |
| ChatGLM2-6B-C-Eval官网  | 51.7 | 48.6 | 60.5 | 51.3 | 49.8 |
| ChatGLM2-6B-该项目  | 50.7 | 47.2 | 60.9 | 60.4 | 50.7 | 47.8 |


关于C-Evaluation的评测教程，推荐参看[tutorial.md](https://github.com/zlpure/CEval/blob/main/tutorial.md)。

测试数据集是CEval，已放到项目的目录下。

运行如下指令进行测试：
```shell
python evaluate_ceval.py
```

> 注意该过程在bf16参数类型下，大概会占用20G左右的显存。

运行结果为[submission.json](https://github.com/zlpure/CEval/blob/main/submission.json)，请按照C-Eval规定的[JSON格式](https://github.com/SJTU-LIT/ceval/blob/main/submission_example.json)保存结果并在 [C-Eval](https://cevalbenchmark.com/) 官网上进行提交。

本项目也同时支持其他大模型在C-Eval上评测，具体修改[evaluate_ceval.py](https://github.com/zlpure/CEval/blob/main/evaluate_ceval.py)文件的第13、14行对应的模型和tokenizer即可。
```python
tokenizer = AutoTokenizer.from_pretrained("/data1/zengliang/chatglm2-6b", trust_remote_code=True)
model = AutoModel.from_pretrained("/data1/zengliang/chatglm2-6b", trust_remote_code=True).bfloat16().cuda()
```
