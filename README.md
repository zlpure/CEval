# C-Eval + ChatGLM2-6B
本项目旨在使用开源的[ChatGLM2-6B](https://github.com/THUDM/ChatGLM2-6B/tree/main)模型，在中文评测框架[C-Evaluation](https://cevalbenchmark.com/)上进行效果评测。

官方评测结果是Average Score 50.1，本项目的结果是50.7，评测结果基本一致。具体结果列表如下：

|  Model  | Average  | STEM | Social  Sciences | Humanities |  Others |  
|  ----  | ----  | ----  |----  |----  |----  |
| ChatGLM2-6B-官网  | 50.1 | 46.4 | 60.4 | 50.6 | 46.9 |
| ChatGLM2-6B-该项目  | 50.7 | 47.2 | 60.9 | 60.4 | 50.7 | 47.8 |


关于C-Evaluation的评测教程，推荐参看[tutorial.md]()

运行如下指令进行测试：
```shell
python evaluate_ceval.py
```

> 注意该过程在bf16参数类型下，大概会占用20G左右的显存。

运行结果为[submission.json]()，请按照C-Eval规定的[JSON格式](https://github.com/SJTU-LIT/ceval/blob/main/submission_example.json)保存结果并在 [C-Eval](https://cevalbenchmark.com/) 官网上进行提交。