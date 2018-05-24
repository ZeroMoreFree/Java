## 文章是我从另外一个网站翻译的，翻译水平有限，共勉。原文链接：[Non-blocking Server](http://tutorials.jenkov.com/java-nio/non-blocking-server.html)

![design](http://tutorials.jenkov.com/images/java-nio/non-blocking-server-4.png)
* 组件通过询问Selector，查看是否有可以阅读的Channel，有的话就返回那个channel实例。一个被选出来的Channel，我们可以把它视为一个data block，我们并不知道这个block里面有多少完整的消息，也许是一条，也是大于或者小于一条，总之，极有可能是不完整的、部分的消息。

* 我们在处理这些不完整的信息的时候，需要做两件事，这两件事都充满了挑战：
  * 我们想要更少的信息拷贝，拷贝的次数越少，则性能越高。
  * 为了使得消息解析的时候更加方便，我们需要把完整的信息存储在连续的字节数组中。
