来宝人工智能：基于树莓派的语音对话机器人
=================

[![Build Status](https://travis-ci.org/jjwang/laibot-client.svg?branch=master)](https://travis-ci.org/jjwang/laibot-client) [![Python3](https://img.shields.io/badge/python-3-blue.svg
)](https://www.python.org)

![PicName](http://115.28.128.30/tjbot.jpg)

如果你喜欢此项目，请打一颗星。

[开发日志](
https://github.com/jjwang/laibot/wiki) [演示视频](http://v.youku.com/v_show/id_XMzIzNDUyNjQ5Mg==.html?spm=a2h3j.8428770.3416059.1)

## 目录

- [项目的由来](#项目的由来)
- [先选定硬件](#先选定硬件)
- [再敲定软件](#再敲定软件)
- [启动来宝](#启动来宝)
- [项目的规矩](#项目的规矩)

本宝邮箱：laibot(at)163.com

## 项目的由来

来宝项目的由来是因为2017年智能音箱太火了！当我在看基于淘宝可购买的硬件电路板以及免费语音服务如何构建智能音箱时，我找到了[japser-client](https://github.com/jasperproject/jasper-client)和[dingdang-robot](https://github.com/wzpan/dingdang-robot)这两个项目。Jasper完成了一个大概的框架，但是没有集成对应的汉语服务；Dingdang基于Jasper继续演进。不得不说，Dingdang开发的确实非常好，集成了很多的服务、编写了大量的文档，使得一个新手很容易入门。

但是，Dingdang并不是我想要的。就智能音箱这个方向来说，众多巨头涌入的是一个2亿的小市场，小市场的由来是因为用户接受度不高（画外音：什么？天猫双十一卖了一百万台？OMG，我可什么都没说）。归根结底，就是现在的汉语普通话智能音箱方案用户体验不佳，说是智能、经常情况下是智障。如果方案在用户体验上没有任何优势，集成了再多的服务实际上用处并不大。

说了这么多，那么来宝想干嘛？其实很简单，来宝就是想试一下基于当前可用的开源软硬件和免费语音服务，能打造的语音助理最好能到什么样子？Jasper和Dingdang从优化的角度来说还做的不够，这些是来宝所想做的。

好吧，这就是来宝的由来！能做到什么程度，说实在的，我也不知道，走走看吧！和Dingdang一样，来宝也基于Jasper。

## 先选定硬件

硬件肯定是基于树莓派了。树莓派是台全功能卡片尺寸电脑，可以运行多种操作系统，支持键盘、鼠标、显示器等。选择树莓派的好处就是即使觉得这个音箱没啥用，还有好多其他有意思的玩法。小朋友可以玩，装个Scratch。喜欢小米产品的大朋友可以玩，装个Home Assistant，恩，成了智能家居控制中心；话说，智能音箱的理想不就是智能家居控制中心么？

既然是智能音箱，音频输入音频输出必不可少。我的选择是：麦克先用单麦，后面再尝试多麦，树莓派的多麦解决方案现在也是多如牛毛了啊！外放用USB微型音箱，不需要外接电源的那种。这样，整个音箱就可以用一根Mini USB线给点亮啦！

另外的一个大问题是造型！无论是Jasper还是Dingdang Robot，造型太挫或是没有造型。一堆线连来连去，看起来乱糟糟的，处女座那是相当的烦心。所以，咱们需要一个专业的外壳。咱没必要外壳用金属，再类似小米发布会普及的、用6000目砂纸细细打磨，说实在的，磨的再亮也没用。那咋搞？3D打印机，咱打印个外壳。

网上可以下载到各种各样的外壳文件去打印，这里不一一赘述了。第一个版本我选的是IBM的TJBot，看起来也是蛮酷的，有个胳膊还能动。

## 再敲定软件

- 软件开发语言是Python。
- 语音识别、语音合成基于百度的服务，需要注册一个开发者账号。
- 众所周知，和语音相比，语义理解难度较小、进入门槛较低，所以本宝希望这部分尽可能由开源代码完成。我申请了新浪云服务、并慷慨投入50元巨资购买了若干云豆，大家后续可以体验。
- 其他似乎也没有什么了，再有的话就看Wiki吧！

## 启动来宝

来宝是基于Jasper的，所以参考Jasper的文档即可；[点击访问Jasper的完整安装、配置和使用指南](
https://github.com/jjwang/laibot/wiki/Jasper%E7%9A%84%E5%AE%89%E8%A3%85%E3%80%81%E9%85%8D%E7%BD%AE%E4%B8%8E%E4%BD%BF%E7%94%A8)。

来宝使用时，先说出唤醒词“OKEY TOMMY”、听到“嘀”的一声后说出语音指令；来宝检测到语音结束会播放“嘟”提示音；稍等片刻后，来宝即会回复。

写完如何启动来宝的介绍性文字后，我才意识到：实际上来宝是很难配置的。
- 第一步的配置障碍就是麦克风和音箱，这步我建议禁掉内置的声卡输出，麦克风和音箱均使用上文推荐的USB外接设备。
- 第二步是各种软件的安装，这个也是相当的繁琐。
- 第三步需要申请百度语音的开发者账号，并填写配置文件。好吧，为方便大家使用，我尽快把我的Key分享出来，先借你用一下。
- 第四步就是运行了。说真的，现在这个版本运行体验不大好，不说“OKEY TOMMY”的成功率、光识别的网络延迟我觉得就有点抓狂；等我共享视频后大家体验一下。我觉得[japser-client](https://github.com/jasperproject/jasper-client)和[dingdang-robot](https://github.com/wzpan/dingdang-robot)延迟应该是一样的大吧，没看到他们做了啥优化。

## 项目的规矩

- 确保通过单元测试。

        python3 -m unittest discover
- Python 代码需符合 PEP 8 编程规范，检查工具使用 flake8。

