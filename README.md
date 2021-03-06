# 项目：平安有你APP
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
- 一句话版本：平安有你APP可以识别到经过设置特定语音样本后会进行自动报警，同时发送紧急短信和定位信息给设置的紧急联系人，在您不知方向时还能够提供自动导航服务，竭尽所能保护您的安全。
- 一分钟版本：平安有你APP旨在让用户在危机情况且无法触碰手机或者不便于操作手机的环境中能够快速报警或快速的通知紧急联系人。同时将自动查找推送安全位置语音指引用户到达。智能推送安全地址能使用户在遭到不利因素时快速进行反应，同时该功能也可以通过语音唤醒开启。同时软件可以记录发生险情时候的声音或影像等，可作为证据保留。

### 核心价值
- 该应用主要针对用户在无法操作手机进行报警的紧急情况。比如（手机被对方夺走的情况），并且可以在后台与紧急联系人实现简单的智能对话，比如交代方位，发送现场的录音文件给对方等。
- 在用户遇到险情后自动向用户推荐距离最近的安全区域（可以是派出所、人多的地方等等）
### 痛点
- 苹果手机报警功能是长按音量键和关机键，一些app也是在能操作手机的情况下才能实现报警，也就是说，这些功能是建立在能近距离接触到手机的情况下才能够使用的
- 用户在遇到紧急情况时难以直接使用手机进行联系，无法及时的传递信息。
- 遇到问题的时候非常慌张，往往无法判断方位，不能及时到达安全的地方。

### 人工智能概率性
- 录音识别结果不准确，语音唤醒功能难开启。
- 用户录入的音频需口齿清晰并简短。

### 使用的api
- **语音识别和语音合成api（百度）**<br>
    1.语音识别<br>
语音识别会识别出机主的声音和特定的内容后才会进行报警,同时，这个语音需要用户进行声纹的录入，只有特定的人的特定语音指令才可以唤醒软件<br>
    2.语音合成<br>
  应用会在识别到用户的报警需求后进行语音播报的确认 如果在五秒内没有取消则自动报警（语音播报确认的功能可以用户自行设置是否需要）
-  **语音唤醒功能**（百度）
特定语音指令唤醒功能，唤醒的同时执行指令操作，可自定义设置多个唤醒词，快捷便利的进行使用。


### 用户需求
|用户案例|API|重要程度|
|:-|:-|:-|
|小丽晚上下班回家，遇到有人抢劫，虽然反应及时并逃跑，但是对方紧随其后，周围也没有人烟，手机在包里无法快速拿出，想要通知男朋友却没有机会|语音唤醒、语音识别|重要|
|小音遇到危险后，并不熟悉周围的地形，需要开启自动导航服务|语音合成|重要|


# 原型
- [平安有你原型](http://hailbucky.gitee.io/api_ml_ai_prototype)
- [平安有你原型下载区](https://github.com/HailBucky/API_ML_AI/tree/master/%E5%B9%B3%E5%AE%89%E6%9C%89%E4%BD%A0_%E5%8E%9F%E5%9E%8B%E4%B8%8B%E8%BD%BD%E5%8C%BA)

# API产品使用
## 产品定价
- 百度语音合成api定价
![语音合成定价](https://github.com/HailBucky/API_ML_AI/blob/master/api语音合成.png)

- 百度语音识别api定价

![语音识别定价](https://github.com/HailBucky/API_ML_AI/blob/master/语音识别.png)

- 腾讯云语音识别api定价
![腾讯云语音识别定价](https://github.com/HailBucky/API_ML_AI/blob/master/%E8%85%BE%E8%AE%AF%E4%BA%91%E5%AE%9A%E4%BB%B7.png)

## 使用比较分析
### 百度-语音识别

- [百度-短语音识别文档](https://ai.baidu.com/tech/speech/asr)
```
from aip import AipSpeech

""" 你的 APPID AK SK """
APP_ID = '18107635'
API_KEY = 'VnRI6FgjHiCkEOAHxPcEq0UG'
SECRET_KEY = 'rXLik8wvXLBcufMdSMcmevmxLtAzKUy3'

client = AipSpeech(APP_ID, API_KEY, SECRET_KEY)

def get_file_content(filePath):
    with open(filePath, 'rb') as fp:
        return fp.read()

# 识别本地文件
client.asr(get_file_content('C:/Users/Hail Bucky/Desktop/xixi1.wav'), 'wav', 16000, {
    'dev_pid': 1536,
})
```
### 输出结果：
```
{'corpus_no': '6774311764074314323',
'err_msg': 'success.',
 'err_no': 0,
 'result': ['拟核辉王红帮我打给王你叫什么名字'],
 'sn': '683704804301577267368'}
```
- 上述代码使用的是百度的语音识别API，录音文件是发音较标准的20秒录音，正确内容为“古代有一书生名为宁采臣”。由结果可以看出识别结果不太准确，词不达意。
- 于是尝试短语音识别看是否可以提高识别准确性。
```
from aip import AipSpeech

""" 你的 APPID AK SK """
APP_ID = '18107635'
API_KEY = 'VnRI6FgjHiCkEOAHxPcEq0UG'
SECRET_KEY = 'rXLik8wvXLBcufMdSMcmevmxLtAzKUy3'

client = AipSpeech(APP_ID, API_KEY, SECRET_KEY)

def get_file_content(filePath):
    with open(filePath, 'rb') as fp:
        return fp.read()

# 识别本地文件
client.asr(get_file_content('C:/Users/Hail Bucky/Desktop/simple.wav'), 'wav', 16000, {
    'dev_pid': 1536,
})
```
### 输出结果：
```
{'corpus_no': '6779569877666691048',
 'err_msg': 'success.',
 'err_no': 0,
 'result': ['嗯嗯你好'],
 'sn': '963224966541578491618'}
 ```
 - 语音内容为“你好”
 - 尝试了短语音后发现准确率高了很多，于是在语音识别和唤醒词的设置上应该尽可能短且清晰。
 
 ### 百度-语音合成
- [百度-在线语音合成](https://ai.baidu.com/ai-doc/SPEECH/fk38y8hqo)
 ```
 from aip import AipSpeech

""" 你的 APPID AK SK """
APP_ID = '18107635'
API_KEY = 'VnRI6FgjHiCkEOAHxPcEq0UG'
SECRET_KEY = 'rXLik8wvXLBcufMdSMcmevmxLtAzKUy3'

client = AipSpeech(APP_ID, API_KEY, SECRET_KEY)

result  = client.synthesis('你好百度', 'zh', 1, {
    'vol': 5,
})

# 识别正确返回语音二进制 错误则返回dict 参照下面错误码
if not isinstance(result, dict):
    with open('auido.mp3', 'wb') as f:
        f.write(result)
        
```
- [语音合成文件查看](https://github.com/HailBucky/API_ML_AI/blob/master/auido.mp3)
- 语音发音清晰，语速正常，认为可以正常的进行使用，也没有报错现象发生。

### 腾讯云语音识别
- [腾讯云网站](https://cloud.tencent.com/)<br>
![腾讯云语音合成](https://github.com/HailBucky/API_ML_AI/blob/master/%E8%85%BE%E8%AE%AF%E4%BA%91%E8%AF%AD%E9%9F%B3%E8%AF%86%E5%88%AB.png)
- 腾讯云的语音识别并非使用代码，而是直接上传音频样本。

- 长语音识别
### 输出结果：
```
[0:0.470,0:4.475,1]  古代有一书生名为宁采臣。
[0:4.475,0:7.005,1]  浙江人品行端正。
[0:7.005,0:10.875,1]  一次他去京华应天色已晚。
[0:10.875,0:14.280,1]  他来到一庙里想要借宿及网。
[0:14.280,0:16.900,1]  这时庙里出来一和尚。
[0:17.010,0:19.550,1]  宁采臣港忙全全。
[0:19.550,0:20.210,0]  
```
- 短语音识别
```
[0:1.040,0:1.940,0]  你好。
```
- 从结果上来看，腾讯云的准确性高了很多非常多，基本的内容都可以进行识别。
## API使用比较结果
- **语音识别**<br>
在api的选择上，语音识别中腾讯云的语音识别准确率更高，无论是复杂一点的长语音还是简短的短语音都要更为准确。百度的识别长语音基本无法进行识别，短语音也有较大的误差。<br>
- **语音合成**<br>
百度的语音合成很清晰。

