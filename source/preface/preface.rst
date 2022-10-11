1.1. 概述
---------
DemoMCS是演示如何使用MA/MCS API触发Metis Station进行各种工作及其组合的Python脚本。
与MCS定义一样，它可以使Metis Station进行捕获、AI处理、记录、解码、编码、推/拉流、回放和预览。

DemoMCS不仅是一个面向半自动测试套件的演示脚本，也是一个帮助最终用户(RD或Tester)
理解如何使用ESWIN MCS restful API和MA API的应用程序。

本文作为 DemoMCS 的使用手册，目标是为了满足客户了解 **MA API** 及
**MCS** 的使用，观看 Metis Station 功能演示，同时辅助进行功能测试的需求.
为了使用MA接口，我们需要借助Postman工具，同时还要花费很多时间去理解以及编写下发的MCS
Json文件，借助DemoMCS脚本与该手册，可以快速了解 **MA API** 与
**MCS** 的功能。

.. seealso::

    如果为了快速上手 **MCS** ，可以直接阅读第4章节 :doc:`Scenario <../scenarios/index>` 。
    如果想了解 **MA API** 并按照自己方式对接口进行封装使用，可以参考第3章节 :doc:`Scripts API <../api/index>` ，
    **MA API** 文档可以在第5章节 :doc:`FAQs <../FAQs/index>` 下载。

1.2. 目的
---------

-  1.当 Metis Live
   遇到问题阻塞，新版本未发布，作为替代Postman调试的工具。同时也是为了丰富
   Metis Live， 作为一种补充，使用不同的MA API。

-  2.可以提供给客户展示，以故事脚本的形式调用MA
   API，通过不同的组合（AI、录制、宫格切换等）体现MA
   API的优越性与灵活性。

-  3.方便SV
   Team对新版本进行快速的冒烟测试，及时发现新版本引入的问题，同时也包含了很多脚本用于回归性测试，
   极大缩短了利用Postman去一个个下发MCS进行测试的时间。

1.3. 脚本目录结构安排
---------------------

.. figure:: picture/directoryNew.png
   :alt: directory

1.3.1. 01_Basic_Tests
~~~~~~~~~~~~~~~~~~~~~

-  **MA_API_Basic_Tests** : 该目录下存放基础的接口API测试，每个脚本与
   **Libraries** 目录下 ``mediadevicelib.py``
   里的接口函数一一对应，将返回的结果以表格的形式打印出来。 详情可参考 :doc:`3.2章节 <../api/mediadevice>`
   DemoMCS演示效果。

-  **SV_Interface_Tests** : 该目录下存放的是对于 **MA** 各个接口 以及
   **MCS** 各个Spec 的拓展测试，包含接口并发，MCS并发等内容。

1.3.2. 02_Data_Driven_Tests
~~~~~~~~~~~~~~~~~~~~~~~~~~~

数据驱动测试，通过下发错误的消息体，或者修改外设环境依次执行相应步骤，查看对应接口返回的内容。

1.3.3. 03_Scenario_Driven_Tests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

故事驱动型测试，S1E1 即 Scenario 1 Episode 1
，每一个目录下包含若干个Action脚本文件，将各个Action 整合一起执行的 ``Act_Story.py`` 脚本，以及
一个用于存放脚本需要下发的MCS模板目录（json_templates目录)。
详细内容可以看第4章节 :doc:`Scenario <../scenarios/index>` 的内容

1.3.4. 04_SV_Regression_Tests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

由SV
Team设计的针对Story场景的回归测试内容。每个测试脚本针对单个功能进行一系列测试，
测试广度相比于 **03_Scenario_Driven_Tests** 有所欠缺，但是深度有所加强。
提前准备了下发的MCS模板，通过脚本带参数的形式修改下发的MCS模板内容，达到测试目的。
该目录下脚本命名规范则是完全按照Case设计的内容以及副标题来命名的，
方便测试人员回归性测试时与测试任务表一 一对应，极大地提高了测试效率。

1.4. 架构
---------

.. figure:: picture/structure.png
   :alt: structure

