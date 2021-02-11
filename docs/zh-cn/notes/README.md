### 你好朋友 👋

这里会记录我的学习笔记。

## 使用注册表文件（REG）

REG是一种注册脚本文件,Regedit注册表编辑器可以使用REG文件来导入、导出注册表的子项和值。并且REG文件可以使用任何文本编辑进行修改，熟悉REG可以起到事半功倍的效果。

[👉注册表👈](zh-cn/notes/reg/Reg.md)<!-- {docsify-ignore} -->

## AI面试百题训练营

各个大厂合计100道经典面试题目：朴素贝叶斯模型、随机森林算法、经典网络框架、决策树、GBDT、k-Means、XGBoost、自然语言处理-Bert等全知识点覆盖

[👉AI面试题笔记👈](zh-cn/notes/ML_notes/)<!-- {docsify-ignore} -->

## Windows组策略配置时间同步

在使用时，通过注册表修改配置时间同步导致每次开机需要手动执行一次时间同步。
!> 在强制关机或意外断电之后，系统不会自动执行时间同步，除非手动触发一次时间同步或正常关机重启一次才可以自动同步时间。
微软推荐使用[Windows系统中时间服务组策略设置时间同步](https://docs.microsoft.com/zh-cn/windows-server/networking/windows-time-service/windows-time-service-tools-and-settings)，只需在Windows中简单配置即可实现电脑之间的时间同步。

[👉组策略配置时间同步步骤👈](zh-cn/notes/time_service/windows_time_servicetools.md)<!-- {docsify-ignore} -->