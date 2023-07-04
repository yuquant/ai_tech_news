## 参考链接
https://www.bilibili.com/video/BV1hd4y187CR/?spm_id_from=333.1007.top_right_bar_window_history.content.click&vd_source=d81f26c1e7ea622b22fa6b5972e25554
https://zhuanlan.zhihu.com/p/590311003
GPT3.5, InstructGPT和ChatGPT的关系https://blog.csdn.net/keeppractice/article/details/129973967
### 要点
- 模型能做什么，很大程度上取决于训练的数据，该模型用了很多类型的问答数据（文本生成、问答、总结、翻译等）
- InstructGPT雇佣了大约40人进行数据标注13000条数据，数据标注也有很多技术细节需要了解，并且有很多相关的文献可以参考
- 在训练阶段，对于标注，一个比较省劲的方法是让模型对各种答案进行一个排序，对于排序的标注是比较省事的
- 大模型训练不稳定，容易梯度爆炸，loss为nan，且软硬件之间还有一些不稳定性因素，
- 少量标注训练一个差不多的模型，再用这个模型进行辅助标注，减少标注工作量
- 排序（PairWiseRankingLoss）比直接分类（n选1）的损失函数能更好应对过拟合问题
- 有三个模型，第一个模型监督学习模型，各种问答；第二个奖励模型，在第一个基础上对输出的答案进行排序，需要人工参与标注；第三个，强化学习（不需要人工标注）模型，随机生成各种数据，让模型自己对答案打分，感觉类似GAN之类的左右手互搏的模型