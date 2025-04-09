# 什么是 repaint？

repaint 的本质就是重新根据分层信息计算了绘制指令。

当改动了可见样式后，就需要重新计算，会引发  repaint。

由于元素的布局信息也属于可见样式，所以 reflow 一定会引起 repaint。