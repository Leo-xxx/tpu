## 重磅！谷歌大脑提出EfficientNet平衡模型扩展三个维度，取得精度-效率的最大化！

CV君 [我爱计算机视觉](javascript:void(0);) *昨天*

点击我爱计算机视觉标星，更快获取CVML新技术

------



今天要跟大家重磅介绍今天谷歌大脑新出的论文《EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks》，在模型扩展时平衡好深度、宽度、分辨率，取得精度、效率、模型大小的最大化。



借由此简单有效的模型扩展方法，作者在使用神经架构搜索得到的基模型上扩展出一系列模型EfficientNets，达到了更好的精度和效率的平衡，其中EfficientNet-B7模型在ImageNet数据集上达到 state-of-the-art 84.4% top-1 / 97.1% top-5 精度，并且相比目前最好的方法模型size减小8.4倍，速度快6.1！！



简直是神级操作！



该文已被ICML 2019录用，这可能是一篇要改变整个深度卷积网络模型设计的论文了。



下面是作者信息：



![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTsgrXMebXP2ibwLMwejyvw78hCib6LQraObEXPDz403b4OJ9ywM9bic0CichRhKYYiadEWqO3ughicRBBbQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



两位作者均来自谷歌大脑。



下图是作者使用该文方法得到的7个EfficientNets与目前知名的state-of-the-art模型精度-参数量的比较：





![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTsgrXMebXP2ibwLMwejyvw78ModiaibtFUibDZMiaM7UTjyzKL8jMZsguAn6RKToPqsibBRkiciaI7ibSW1lxg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



可见本文得到的模型在相近模型大小时，精度高于所有之前的竞争对手！



**什么是模型扩展？**



模型扩展是借由改变深度卷积网络的宽度、深度、分辨率进而寻找更高精度模型，或者精度-计算量-模型size满足一定要求的这种方案模型的方法。



下图展示了这一过程：



![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTsgrXMebXP2ibwLMwejyvw78sibH6Man6gVItCmUibJFoBIOK1xTVHmSmsLCyLKMskH94qDEoN3JiaVcQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



其中最右为作者提出的方案，及在三个维度（宽度、深度、分辨率）进行复合扩展。

（模型扩展是很常见的操作，只是之前大家总是关注在宽度和深度，作者在这里将分辨率纳入考虑）



这是作者做的实验，单一调整一个维度能够获得精度提升，随着参数调的越大，精度增益越平滑，即改进不再明显。



![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTsgrXMebXP2ibwLMwejyvw78b7ibAzHXZHFnhLKzMl38AMSMkNhicadfkwK0fib8ulTU15ibibXlfhCQiaUg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



下图为同时调整深度和分辨率获得的模型的结果，可见联合调整能够获得更好的精度增益曲线。



![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTsgrXMebXP2ibwLMwejyvw78RDvmclicfA4uMOYnMJKtVat7D3ibfWOsXpiclrhrUazdH3cPIPYCXEyGQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)





**方法**



作者就是把深度d、宽度w和分辨率r纳入一个受限的搜索空间，如下：



![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTsgrXMebXP2ibwLMwejyvw78c4SCFmeIPZjzzJ4ln3GWjzwIibtDfiajpjB0vvUiaEZ4OibgfWXKP9yJLg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



对于特定的基模型，采用如下两个步骤获得一系列扩展模型，从计算量参数量小精度低到计算量参数量大精度高的一些列模型。



![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTsgrXMebXP2ibwLMwejyvw784q0wc2xylNaOveBlNJWIx0jasxfTyVeTfvxF4q5iaNqsJibmiacZAFWOQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



下面是作者用神经网络搜索得到的基模型EfficientNet-B0。



![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTsgrXMebXP2ibwLMwejyvw78uZAKuDj5rib8PeBESk43muuy5QJ3tNnQun5xwuU1rXFVCnHicrCmpB7g/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



**实验结果**



实验结果实在是太靓丽了！



这是作者得到的七个模型与现有最好的算法在ImageNet数据集上的比较，在精度超越的同时，计算复杂度和参数量都下降了一个数量级！



![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTsgrXMebXP2ibwLMwejyvw78XuDYzlm5mwS6emRCB7EHvLr5iadXuaJoU79VUrmOMm8FmqibLbRn0pdQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



下图为在MobileNets和ResNet上与单一维度扩展的比较，计算量相近的情况下，本文方法精度一致性的更高！



![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTsgrXMebXP2ibwLMwejyvw788qTbv2ncgL1wCmwcATcsaB9zkISCFBfaMVnV9Okgibb21UxMHZNPdcw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



在实际的硬件上计算同样验证了理论的结论：



![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTsgrXMebXP2ibwLMwejyvw78THoYCAhZAFxeOHXPKslr1mfNWHYPNLsbDHe0NNjxnObMs9Tw74nJDQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



作者用得到的新模型在8个数据集上进行了迁移学习实验，取得了5个state-of-the-art的结果，而且计算量和参数量依旧小一个数量级！



![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTsgrXMebXP2ibwLMwejyvw78rFHl9OOyOuYtmRFBANJRXibN6ia1sHX3TvCrh8myGANicibhAGuSezoHBA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



该算法虽然简单，但结果实在是太吸引人了，强烈推荐大家关注！



论文地址：

https://arxiv.org/pdf/1905.11946v1.pdf

开源地址：

https://github.com/tensorflow/tpu/tree/master/models/official/efficientnet



**专业交流群**



关注最新计算机视觉与机器学习技术，欢迎加入52CV专业交流群，扫码添加CV君拉你入群，



**（请务必注明:52CV）：**

**![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTs1Ke4WXicIqN7QibMXL527MCvicgajlnePVw1mnomoLqFqL0WLf7UUpSkVGj2E1GGe83e8ZmY0G42jw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)**

喜欢在QQ交流的童鞋可以加52CV官方QQ群：702781905。

（不会时时在线，如果没能及时通过还请见谅）



------





![img](https://mmbiz.qpic.cn/mmbiz_png/BJbRvwibeSTvVOnJBvePcP1qFUSWpyvrjpYAWNIZTZzUA7Zq4VPlReicJWcIeozxic5VhHlwNQNAFXmKQBtKf5xAQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

长按关注我爱计算机视觉









微信扫一扫
关注该公众号