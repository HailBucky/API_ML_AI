# 项目：智能报警APP
# PRD 产品需求文档
---
|发布日期|2019/12|
|:-|:-:|
|项目名称|智能报警APP|
|文档状态|进行中|
|Document owner|陈梦瑶|
|Designer|陈梦瑶|
|Developer|陈梦瑶|
|QA|陈梦瑶|

## 产品定位
能够通过语音进行报警，并提供指引帮助用户脱险的智能app
## 加值宣言
该产品旨在让用户在危机情况且无法触碰手机或者不便于操作手机的环境中能够快速报警或快速的通知紧急联系人。同时将自动查找推送安全位置语音指引用户到达。

### 价值主张
该应用识别到经过设置特定语音样本后会进行自动报警，同时发送紧急短信和定位信息给设置的紧急联系人。

### 核心价值
该应用主要针对用户在无法操作手机进行报警的紧急情况。比如（手机被对方夺走的情况），并且可以在后台与紧急联系人实现简单的智能对话，比如交代方位，发送现场的录音文件给对方等。
在用户遇到险情后自动向用户推荐距离最近的安全区域（可以是派出所、人多的地方等等）
### 痛点
- 苹果手机报警功能是长按音量键和关机键，一些app也是在能操作手机的情况下才能实现报警，也就是说，这些功能是建立在能近距离接触到手机的情况下才能够使用的
- 用户在遇到紧急情况时难以直接使用手机进行联系，无法及时的传递信息。
- 遇到问题的时候非常慌张，往往无法判断方位，及时到达安全的地方。

### 使用的api
- 语音识别和语音合成api（百度）<br>
    1.语音识别<br>
语音识别会识别出机主的声音和特定的内容后才会进行报警,同时，这个语音需要用户进行声纹的录入，只有特定的人的特定语音指令才可以唤醒软件<br>
    2.语音合成
  应用会在识别到用户的报警需求后进行语音播报的确认 如果在五秒内没有取消则自动报警（语音播报确认的功能可以用户自行设置是否需要）
-  语音唤醒功能（百度）
特定语音指令唤醒功能，唤醒的同时执行指令操作，可自定义设置多个唤醒词，快捷便利的进行使用。
- 问答系统（图灵机器人）
通过关键词等识别用户询问的问题并进行回复。比如当紧急联系人需要了解使用者的情况，将会发送实时录音以及路程计划。

### 用户需求
|用户案例|API|重要程度|
|:-|:-|:-|
|小丽晚上下班回家，遇到有人抢劫，虽然反应及时并逃跑，但是对方紧随其后，周围也没有人烟，手机在包里无法快速拿出，想要通知男朋友却没有机会|语音唤醒、语音实现|重要|
|小杜收到女朋友手机上发来的紧急情况，他很着急想了解对方的安危和发生的情况，但对方此时无法接听电话|问答系统|重要|


# 原型

![原型首页](https://github.com/HailBucky/API_ML_AI/blob/master/原型1.png)

# API产品使用
## 产品定价
- 百度语音合成api定价
![语音合成定价](https://github.com/HailBucky/API_ML_AI/blob/master/api语音合成.png)

- 百度语音识别api定价

![语音识别定价]()
- 图灵机器人定价
![图灵机器人定价](https://github.com/HailBucky/API_ML_AI/blob/master/api1.png)

## 使用比较分析
