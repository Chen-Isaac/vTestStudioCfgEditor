###使用vTESTstudio和vTestStudioCfgEditor生成的配置文件进行测试的方法

1. 打开vTESTstudio，在菜单栏上选择**New Project**。

    ![](https://ooo.0o0.ooo/2017/11/09/5a03d031dab74.png)

    选择路径和项目名称后，保存。

    ![](https://ooo.0o0.ooo/2017/11/09/5a0432e461011.png)

2. 在Project View下右击新项目，在弹出菜单中选择**New Test Unit**。

    ![](https://i.loli.net/2017/11/09/5a03d139636fb.png)

    为新建的Unit取一个恰当的名字。

    ![](https://i.loli.net/2017/11/09/5a0433a7a3330.png)

3. 在当前Project View的Test Unit下，右键，新建一个Test Table。

    ![](https://ooo.0o0.ooo/2017/11/09/5a04346f8f3d1.png)

    为新建的Table取一个恰当的名字。Test Table作为Test Case编排的主界面，你可以将它类比为一个大型程序的main函数入口。

    ![](https://i.loli.net/2017/11/10/5a04fada745b9.png)

4. 将之前运行\_testStepCfgEditor.vi时生成的basicFunctionTest.can文件放置在和step3中生成的Table文件同一的路径下。然后，在当前Project View的Test Unit下，右键，选择Add Existing File。

    ![](https://i.loli.net/2017/11/10/5a04fda17422c.png)

    选择basicFunctionTest.can，点击ok，完成添加。

    ![](https://i.loli.net/2017/11/10/5a04ffd3f3ede.png)

5. 在项目目录下新建cfg目录，将之前vTestStudioCfgEditor应用中生成的paraCfg.ini和testStepCfg.ini这两个配置文件，复制黏贴到该目录下；

    ![](https://i.loli.net/2017/11/09/5a03ef0132608.png)

6. 打开该项目的CANoe工程，在configuration菜单栏下选择System Variables。

    ![](https://i.loli.net/2017/11/09/5a03efeedf0ee.png)

    在打开界面的User-Defined一栏，新建iniParaCfgPath和iniTestStepCfgPath这两个自定义的系统变量。其中，Data Type全部设成String，Initial Value分别设成paraCfg.ini和testStepCfg.ini所在的路径，Read Only属性全部设成Read Only，如下图所示：

    ![](https://i.loli.net/2017/11/09/5a03f1556431a.png)

7. 返回vTESTstudio，在菜单栏Tools中选择**Import CANoe Environment**下的Import System Environment and Symbols，将CANoe工程中的系统变量和环境变量导入vTESTstudio项目。

    ![](https://i.loli.net/2017/11/09/5a03f6faada10.png)

    导入成功后，Symbols一栏应该会出现CANoe中的database及系统变量等讯息，如下图所示：

    ![](https://i.loli.net/2017/11/10/5a0506287760f.png)

8. 在Project View下，点击进入Test Table。在其中的Test Tree下，就可以根据需要，开始编排选取Test Case。各Test Case的具体内容之前已经在testStepCfg.ini中被配置完成。用户只需在Test Tree下方，点击各栏目中的小三角，就可以选择testStepCfg.ini中已配置好的Test Case。

    ![](https://i.loli.net/2017/11/09/5a03f971545b0.png)

    如果想要选择的某个Test Case在下拉栏中有含list和不含list的情况，请选择含list的Test Case。选定后，Test Case右侧会出现针对Case的参数配置栏。

    ![](https://i.loli.net/2017/11/09/5a03fc9a1dcb2.png)

9. 如果该Case的参数是孤立的，仅仅在一个Case中使用，那可以在参数配置栏的该参数下，选择Type of Values为Single Values，然后将该参数在测试中可能的取值填入，如下图所示：

    ![](https://i.loli.net/2017/11/10/5a050ecd4ef74.png)

    但是，如果该参数及其可能取值，会运用到后续多个Test Case中的话，则建议创建一个Parameter File，将多个Case会共用的参数配置其中，这样后续使用起来会方便得多。你可以将Parameter File里的参数理解成C语言中的宏定义。

10. 在当前Project View的Test Unit下，右键，新建一个Parameter File。

    ![](https://i.loli.net/2017/11/09/5a03fe6bd2c83.png)

    为新建的Parameter File取一个恰当的名字。

    ![](https://i.loli.net/2017/11/10/5a0510f277496.png)

11. 在Parameter File中，选择insert list，添加新参数。

    ![](https://i.loli.net/2017/11/10/5a0511e076389.png)

    type选择String，建立各参数的可能取值集合，如下图所示；

    ![](https://i.loli.net/2017/11/09/5a0403c066f1d.png)

12. Parameter File配置完成后，就可以在Test Case右侧的Case参数配置栏中进行相应的配置了。对于需要选取Parameter File中参数的场合，需先在Type of Values一栏选择List from Parameter File，然后就可在Value Source中选取该参数。

    需要注意的是，这配置栏中的Combinatorics如果是选择Sequential，则参数间的组合是以将同一行的参数值配置成一个case；如果选择Combinatorial，则会将这三列的参数值按排列组合的方式生成相应参数值组合的case。具体的选择依据实际需求和参数栏中Values的配置方式。

    ![](https://i.loli.net/2017/11/09/5a0414df5af99.png)

13. 当Test Tree中的Test Case及Case相应参数都配置完成后，在vTESTstudio中点击Build Test Unit按钮或按快捷键shift+F6，进行build。

    ![](https://i.loli.net/2017/11/10/5a05156fb32da.png)

    如果build成功，则在vTESTstudio下方的Output一栏，会显示某vtuexe文件已被创建，Build succeeded之类的字样。

    ![](https://i.loli.net/2017/11/10/5a0516d77521c.png)

    如果创建失败，会显示Build failed之类的字样。双击Output中的Error字眼，界面会指向错误出现的地方。

14. vtuexe文件创建成功后，再次进入CANoe工程。在View菜单栏中，选择Test Setup下的Test Configurations for Test Units。

    ![](https://i.loli.net/2017/11/09/5a03f408dd5b3.png)

    在弹出的窗口中，点击左上方的加号，新建一个Test Unit，取一个合适的名字；

    ![](https://i.loli.net/2017/11/09/5a03f529ea5a1.png)

    在弹出的窗口右上方，选择加号按钮，将之前生成的vtuexe文件导入。

    ![](https://i.loli.net/2017/11/09/5a0417c9ca367.png)

    导入后的详情见下图：

    ![](https://i.loli.net/2017/11/09/5a04194f50dc2.png)

    因为上例中我在配置的Combinatorics一栏选择了Combinatorial，所以最终这个case匹配出了4\*1\*11=44中组合。具体运行的时候，可以勾选需要的case来运行。

15. 点击CANoe菜单栏下方的Start按钮(闪电图标)，或者使用快捷键F9，会发现Unit上方的开始按钮由灰变红。

    ![](https://i.loli.net/2017/11/10/5a051d3167dee.png)

    勾选你希望此次执行的Case，然后按上图的Start按钮，开始测试。每个Case在测试中花费的时间会标注于右侧，并且测试结果成功的Case会被标注绿色的勾，如果失败，会被标注为红色的叉。

    ![](https://i.loli.net/2017/11/10/5a051e148f984.png)

    测试完成后，点击Unit右上方的Test Report按钮，可以查看测试过程的报告。

    ![](https://i.loli.net/2017/11/10/5a051ea92bc45.png)