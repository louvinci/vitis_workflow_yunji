## HLS and Vitis部署
:dog:首先说明，HLS为high-level synthesis，是一种C/C++语言配合+program(指导命令)，然后借助工具转化为RTL(Verilog/VHDL)的语言描述。
- HLS语言的学习，主要是来掌握不同pragram的用法：也就是如何指导C语言代码转化为对应的硬件代码。常见的有``PIPELINE``\ ``UNROLL`` 流水化\并行展开等命令。
- HLS主要用于编写硬件计算核心（kernel），还需配合一些AXI桥、内存控制接口等构建SoC，最后将整个加速器系统转化为RTL。之后，还需要借助Vitis工具，转化为FPGA bitstream烧录FPGA，并行配合驱动程序完成，可运行加速器。
----

### 1、HLS编程入门参考
**学习目的**：主要是会使用```interface```以及```pipeline```以及```unroll```和```array partition```pragma的使用，完成c->verilog的指导。
- :one:新版本： [UG1399](https://docs.amd.com/r/2022.2-%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87/ug1399-vitis-hls/%E7%AE%80%E4%BB%8B) 编程指南。19/20的老版本可以参考UG902
- :two:[B站视频:arrow_forward:](https://www.bilibili.com/video/BV1J5411t7uE?spm_id_from=333.788.videopod.episodes&vd_source=459f25d1b71e72fac82c5bee26e60bb7&p=2)；文档中不理解的，可以看看视频讲解。快进观看。
-  :three: 《并行程序编程》**知识密度较高**， 官方以一些简单算法加速为例，讲述了pragma的影响：https://xupsh.github.io/pp4fpgas-cn/01-Introduction.html
:bell:可以找一个例子学习一下,适合对pragma的基本语义了解之后阅读。

- 其他HLS学习资料:arrow_right:不建议阅读了
https://rec.ustc.edu.cn/share/690b5610-8cac-11ef-be09-8fe3c6ad0641  内部学习hls的视频。自己可以观看学习，请勿外传

---
### 2、Vitis/Vivado部署工具学习
建议学习顺序：
- :one: 基础细节的工作流 https://github.com/louvinci/vitis_workflow_yunji
- :two: 更全面的部署介绍 https://github.com/Reconfigurable-Computing/Vitis_workflow
-  上述两个文档中间省略了很多高级功能，未涉及部分:arrow_forward: UG1393；官方教程：https://docs.amd.com/v/u/zh-CN/ug1393-vitis-application-acceleration
- :abc: 比较老的部署流程(可以不看)：hls+vivado soc设计 搭建硬件系统并部署至FPGA的。可以参考我写的教程：https://github.com/louvinci/HLStoFPGA
---
### 概念方面：

- tansformer论文解读：https://www.bilibili.com/video/BV1pu411o7BE/?spm_id_from=333.999.0.0&vd_source=459f25d1b71e72fac82c5bee26e60bb7
- ViT论文解读：https://www.bilibili.com/video/BV15P4y137jb/?spm_id_from=333.999.0.0&vd_source=459f25d1b71e72fac82c5bee26e60bb7

- 数据流（dataflow）
ICCAD20:GAMMA: Automating the HWMapping of DNN Models on Accelerators via Genetic Algorithm
ASPLOS2023: FLAT: An Optimized Dataflow for Mitigating Attention Bottlenecks
---
### 工程参考
#### 1、纯HLS工程参考
- Transformer的前馈过程部署：https://github.com/cjg91/trans-fat
#### 2、完整加速器部署流程
- ViT加速器推理过程（**建议学习**）
https://github.com/DJ000011/UbiMoE
----
ps:以上内容作为参考即可，可根据自身情况调整，保持交流
