# OSA-with-WorkersforLabVIEW
 使用WorkersforLabVIEW框架，实现对多种不同类型光谱仪设备操作、读取及数据保存


### 动机
  实验室的多台光谱仪缺少后续代码维护与改进，面临如下问题：
    1. 多个光谱仪配套的LabVIEW程序接口不统一，使用和管理起来很麻烦
    2. 范例程序无法做到实时采集/高速解调
    3. 扩展性差
### 目的
    1. 引入 面向对象，将各个光谱仪封装起来，后续只需调用 .initial 以及 .start_grab 这样方法，就可以实现连续采集
    2. 采用插件的思路，对于后续不同传感器使用的不同解调方法 同样实现封装，后续操作员只需要专注于实现自己解调算法的vi即可
    3. 高速采集 近实时采集（意味着生产者/消费者模式的必要性）

### 想法与尝试
最初打算是 使用LVOOP面向对象方法  + 生产者/消费者 模型 实现对各个光谱仪的封装。但是着实不是一个简单的事情。其一，异步循环 队列消息机 （DQMH）不够模块化，程序较大时 整体框图依旧很乱，再者后续扩展性也不强
接着 考虑 Actor Framework  该框架确实可以满足需求，但是模型很是复杂，学习曲线陡峭，也不是最佳选择
经过网上搜索 找到了 Workers for LabVIEW 这一框架，基本可以实现我的所有需求：

[WorkersforLabVIEW](https://docs.workersforlabview.io/)
![Static Badge](https://img.shields.io/badge/LabVIEW-Workers-brightgreen)

优点：
1. 模块化
2. 扩展性强
（笔者使用的为此时最新的 workers 5.0 开发环境为 LabVIEW 2021 及 2022）


#### 当前状态：
主动开发中！
![Example Image](image/hl720.png)