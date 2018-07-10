* prepareRefresh()：// 准备工作，记录下容器的启动时间、标记“已启动”状态、处理配置文件中的占位符
  * 记录启动时间，
  * 将 active 属性设置为 true，closed 属性设置为 false，它们都是 AtomicBoolean 类型
  * 校验 xml 配置文件
