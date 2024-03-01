# ottospeak.py

基于pydub + gradio的人声采样“硬”拼接工具。

![Static Badge](https://img.shields.io/badge/Python-3.10-blue?style=flat) 

---

## 😕这是什么？

ottospeak.py是一个用于将预先制作的采样包以令人忍俊不禁的方式进行拼接的小工具。

啊你这时就可能要问了，🤓主播主播我们都有RVC了直接炼RVC不好吗。啊你要炼当然是可以的，但是这个，这个就缺了一点味道。

所以这个工具存在的价值，就是让你以🐖✒️都能学会怎么用的方式一键合成~~DSSQ~~莫名其妙的音频。

## 🧐原理？

ottospeak.py会自动读取在`samples/`目录下的所有采样包，采样包由完整的连续采样和`*采样包名.json`标注文件构成，标注文件内标明了采样的内容、标记名、各音素时长等等信息。

在你传入了ottolang格式的语句后，ottospeak.py会自动解析并按规则匹配到相对合理的采样生成一个拼接字典。最终生成一串完整的渲染列表传入`ottorender.py`进行拼接渲染。

## 💩Haw 2 yuus¿

你是一个聪明的用户，你知道用打包好的懒人包是最省事的方案，你只需要双击`start.bat`/`start.sh`就能享受成功的人生，赢！

ottospeak.py的WebGUI的默认监听地址为`localhost:18516`，正常来讲浏览器应该会自动打开这个页面，你也可以手动打开，没差就是了。

如果你不想使用预先打包好了所有依赖的懒人整合包并且觉得自己装依赖这件事很cool，你可以打开你引以为傲的命令行用如下的方式手动装B：

```shell
pip install -r requirements.txt
```

然后你只需要像这样：

```shell
python ottospeak.py
```

袜嗷，你成功启动了ottospeak的web gui！你真是太棒了！

### 🥰进阶用法

ottospeak.py可以被引入作为一个模块来快速的合成一些若至语音，为了用起来更方便，ottospeak.py提供了一个非常简单的入口函数`speak()`。

`speak()`函数接受字符串形式的ottolang语句，返回渲染好的音频对象。可以接受的参数如下：

| 参数         | 类型   | 默认值   | 简介                     |
|------------|------|-------|------------------------|
| `ottolang` | str  | /     | 需要渲染的ottolang语句        |
| `is_save`  | bool | False | 是否将渲染好的音频保存到results目录下 |

使用时，你只需要将ottospeak.py、ottorender.py以及采样包放到需要的地方，然后：

```python
from ottospeak import speak

output = speak('shuo de dao li')
```

### 🤖在Bot中使用？

对于NoneBot有封装好的ottospeak插件，可以直接引入插件使用。

~~其实就是因为听到其他bot合成的电棍过于难绷于是想做一个更好的电棍语音合成Bot插件，最后干脆写成了这个。~~