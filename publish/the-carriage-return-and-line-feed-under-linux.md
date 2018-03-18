> ## 概念定义

这两个概念都来自于以前的电传打字机（teletype model 33）。

回车（carriage return）: 告诉打字机把打印头定位在左边界。

换行（line feed）: 告诉打印机把纸向下移动一行。

> ## 不同系统之间的差别

不同系统对每行结尾的处理有所不同。

linux/unix:  <换行> 即“\n” 对应的ASCII码为“`0x0d`”

windows: <换行><回车> 即“\n\r” 对应的ASCII码为“`0x0d 0x0a`”

mac os： <回车> 即"\r” 对应的ASCII码为"`0x0a`"

> ## 这种差异会导致的问题

- 在linux下用VIM打开windows下创建的文件的时候，每行最后会出现^M。

- 在windows下用记事本打开linux下创建的文件的时候，会导致文件变成一行，不换行。