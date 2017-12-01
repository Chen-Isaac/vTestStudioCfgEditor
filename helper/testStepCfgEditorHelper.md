###_testStepCfgEditor的使用说明

1. 确认工程中所有VI处于关闭状态，然后运行builder。注意，一定要保证工程中所有VI处于关闭状态，不然主VI运行会有异常，面板不能正常显示。

    ![](https://i.loli.net/2017/11/13/5a09371aa9134.png)

2. 点击弹出应用左上角的运行按钮，在菜单栏Editor选择testStepCfgEditor。

    ![](https://i.loli.net/2017/11/13/5a0939d221b85.png)

3. 在随后弹出的窗口中可以选择加载已有的\_testStepCfg.ini文件进行后续的修改，或者可以在vTestStudioCfgEditor\cfg中新建空白的ini文件导入，从头制作一个新的\_testStepCfg.ini文件.注意，必须导入一个存在的文档，无论是否空白。选择完毕，点击确认键。

    ![](https://i.loli.net/2017/11/13/5a093d88e52ba.png)

4. 导入ini文件后，check一栏会显示相应的语法检测结果，如果出现数据类型不匹配或者数目不匹配或者符号格式等错误，check一栏会打上红色的×，并且会标注错误原因；检测正确的话，则会标注绿色的√。

    下图中同时包含有检测正确和错误的图示。需要注意的是，由于屏幕所限，每一列的宽度可能不足够展示该栏全部的信息，这个时候可以用鼠标双击你希望获得清楚信息的行，则该行每一栏的信息都会清晰地放大到上方的VIEW控件中。以下图为例，它展示的就是出错一行的每一栏的详细信息。

    ![](https://i.loli.net/2017/11/10/5a0546ee44d2b.png)
    
5. 修正之前内容的时候，如果需要在两行之间插入新的一行，或者删除某一行内容，可以将鼠标置于表格部分相应的行上，按右键，会弹出一个菜单，根据具体需求，在菜单中选择“在前面插入行”或“删除行”。注意，不要对列进行操作，如果不慎操作错误，请在菜单栏中选择exit退出，再重新启动应用程序，导入testStepCfgEditor。

    ![](https://ooo.0o0.ooo/2017/11/13/5a09401d3076e.png)

6. 在空白处填写新增内容，如果需要插入函数的话，先点击鼠标左键，将鼠标置于该行任一栏内，点击面板右侧的tree控件里具体的某个函数，这时候该函数和具体的参数说明就会被添加到该行相应的栏内。详情参考以下操作图例。

    ![](https://i.loli.net/2017/11/10/5a0553af9d27e.gif)

7. 在空白处填写新增内容，填写完毕后，如果需要查看该行check一栏的判定结果，只需将鼠标点击到除此行以外的其他任意行上，就能立刻看到该行check栏上的判定结果。如果需要查看该行的详细信息，只需鼠标左键双击该行，就可以在上部view控件栏上显示该行所有栏目的详细内容。详情参考以下操作图例。

    ![](https://i.loli.net/2017/11/10/5a05693f35b39.gif)

8. 当所需数据内容全部添加到表格后，点击面板右上角的一个钢笔形状的图标（图标上方标注有Generate testStepCfg.ini）。此刻如果程序检测到之前check一列没有任何错误标记，则该表格生成的ini文件会覆盖并更新之前导入的ini文件；如果发现check一栏的错误尚有还未被更正的情况，程序会弹出提示框提示错误所在行，您可以选择忽视错误继续更新/生成ini文档。或者选择否，不生成文档，回头修改错误。建议，如果没有特殊情况，还请先修复错误后再选择生成文档，否则某些格式错误可能造成生成文档中某些部分的格式和您预想的不一致的情况。以下是错误提醒弹出框的视图：

    ![](https://i.loli.net/2017/11/10/5a056594d7ccf.png)

9. 当ini文件生成成功后，可以点击菜单栏上的exit按钮退出，或者点击菜单栏进行其他操作。注意，当\_testStepCfgEditor还没有运行结束时（生成ini文件后才算正常结束），是不可以在菜单栏创建新的\_testStepCfgEditor或者paraCfgEditor操作的，否则会弹出提示框，提示该VI进程仍然在运行中，必须结束该进程才可以进行其他操作（不限于帮助菜单，帮助菜单上的选项随时都可以按）。提示窗口如下图所示：

    ![](https://ooo.0o0.ooo/2017/11/10/5a0569d526e5e.png)

###_testStepCfgEditor的表格组成

_testStepCfgEditor的表格由6个栏目组成，分别是section，function，function arguments，function parameters，check以及comment。

下面对每个栏目的意义做分类解释：

1. section

    - section对应的即是ini文件中的section，在这个测试架构中，一个section对应的是一个testcase条目。
    
        ![](https://i.loli.net/2017/11/10/5a05551da2726.png)

    - section一栏为空的行，归属于该列以上第一个section一栏不空的行所处的section，如下图所示：

        ![](https://i.loli.net/2017/09/22/59c484444ad75.png)

2. function

    function对应的即是函数，每一个函数实现一个特定的功能，基本上面板右侧的tree控件上已经包含了足够的测试用函数，而且这里函数的基本功能绝大多数都可以通过其名称得到一个大致的了解。用鼠标单击确认需要添加function的行，然后双击右侧面板tree控件上的function，即可自动填入function。当然你非要手写也没有问题，不过需要注意的是，这一栏唯一的限制是，这里可供填入的函数，必须存在于tree控件上。如果填入的函数不存在于tree控件上（比如你坚持手写但是不小心写错了），那么系统会报相应的错误。

    下图是双击tree控件添加函数的过程：

    ![](https://i.loli.net/2017/11/10/5a05562f6c147.gif)

    如果是你自己填，函数名填错了，那么check栏会提示你函数输入错误：

    ![](https://i.loli.net/2017/11/10/5a05573fa16fb.gif)

3. function arguments

    function arguments即对应函数的实参，可以参考第三栏function parameters的形参样式来填入。如果填入的实参和形参的数据类型不符或者数目不符，check一栏会提示相应的错误。

    以下是一个实参与形参数目不符，报错的例子：

    ![](https://i.loli.net/2017/11/10/5a05586f59f86.png)

    以下是一个实参与形参数据类型不符，报错的例子：

    ![](https://i.loli.net/2017/11/10/5a05593b679c9.png)

4. function parameters

    function parameters即对应函数的形参，当你点击面板右侧tree控件添加函数的时候，该函数的形参会自动添加到该栏。填写函数实参的时候，可以参考该栏内容，填入正确类型的实参。需要注意的是，function parameters一栏的存在，仅仅是为了辅助用户填写实参。在最终生成的ini文档中，是没有形参的位置的。

5. comment

    comment即注释，适当的注释有利于用户回顾编写测试内容时的逻辑。这部分内容也会保留在最终生成的ini文件中，跟随在文本行末尾;//符号的后面。注：//的目的只是为了方便识别注释，真正区分注释和正文的关键在于；号。因此，即便用户在comment一栏中的起始没有填入符号//，脚本编辑器最终也会在生成的ini文件中，将符号//补上。

    以下是comment在应用和生成ini文件中的对应位置：

    ![](https://i.loli.net/2017/11/10/5a055a4ed460e.png)

###_testStepCfgEditor的特殊格式说明

1. 首字符带\*的section

    section一栏的字符串中，如果首字符为\*，则说明该section所包含的测试序列可以作为一个变量被后续的首字符不含\*的正常section单独调用。

    举例说明，以下是一个首字符为\*的section：\*switchOffByLockSignal，这个case的功能是通过Lock signal来熄灭氛围灯。

    ![](https://i.loli.net/2017/11/10/5a055b578b2bb.png)

    鉴于灭灯是一个测试中经常需要用到的动作，如果每一次灭灯都需要重复\*switchOffByLockSignal中的这5个动作，显然非常不经济。但是如果将这5个动作放到一个首字符带\*的section中，那么将来灭灯只需要引用\*switchOffByLockSignal这个section的名称，即可实现对这5个动作的调用。

    调用格式： 在section中需要调用的行的function arguments一栏，填入：首字符为\*的section名称，后面加上=号即可完成调用。如下图所示：

    ![](https://i.loli.net/2017/11/10/5a057604ecdb6.png)

    如果调用格式不对，check一栏会报相应的错误，并指示正确的填入方法。如下图所示，调用section的末尾漏掉了=号。

    ![](https://i.loli.net/2017/11/10/5a055ccab6349.png)

    需要注意的是：首字符带\*的section里，不应该再包含有其他的首字符带\*的section，以防止递归等情况下section的互相调用可能造成的死循环。如果在编辑器中出现这个问题，那么check一栏会自动报错。

2. 带\*号的实参

    某些情况下，某几个test case可能互相之间除了个别参数的数值是不同的，其余部分都是相同的，这种情况下，如果分别为这几个case撰写专门的用例肯定是不经济的。那么这时候，用户就可以采用带\*号的实参来处理这种情况，并且程序会自动默认这是一个符合函数形参数据类型的变量。

    其实带\*号的实参的本质目的是占位，延迟决定其指代数值。延迟到什么时候呢？延迟到生成.can文件后，待导入vTESTstudio，再由用户在vTESTstudio的parameter values面板中根据需求自行设定。那么具体是如何过渡到这个步骤的，我们会在后续部分详细说明。

    以下这个例子中，用例chkDrivingModeReqSigImpWhenIgnOff，调用了\*switchOnByDoorOpenSignalWithCheckWhenIgnOff和\*switchOffByLockSignal这两个case，如下图所示：

    ![](https://i.loli.net/2017/11/10/5a055ef280839.png)

    其中\*switchOnByDoorOpenSignalWithCheckWhenIgnOff这个被调用的case详情如下图所示：

    ![](https://i.loli.net/2017/11/10/5a055fc6ec3dc.png)

    \*switchOffByLockSignal这个被调用的case详情如下图所示：

    ![](https://i.loli.net/2017/11/10/5a05605249a87.png)

    终上可以看出，用例chkDrivingModeReqSigImpWhenIgnOff中，一共有\*doorSignal,\*msWaitForTurnOn和\*drvModeReqVal这三个实参变量。
    
    那么，最终当用户使用vTESTstudio来调用这个case的时候，就可以通过vTESTstudio右侧自带的parameter Values面板，将相应的各实参可能的取值填入，然后由Combinatorics一栏来决定这三个参数间的数值匹配方式。

    ![](https://i.loli.net/2017/09/25/59c872cd2cd30.png)

3. 带|号的function

    某些情况下，从产品的某个状态，进入到产品的另一个状态，这个中间可以实现的方式可能不止一种。譬如需求文档中的状态机，就是一个很典型的例子。那么这个情况下，可以选择带|号的function来标注，这是实现状态的另一个路径。

    以下是一个采用了带|号的function的测试用例，其中带|号的function可以理解成上头第一个不带|号的function的另一个实现路径。

    ![](https://i.loli.net/2017/11/10/5a0577e6d223a.png)

    其对应生成的ini文件如下图所示。譬如上图中第三行开始的signalSetting，|wait和|vtSysPwrSupVoltSet这几个函数，到了生成的ini文件中，就分别对应了step2中的3个不同的实现路径。

    ![](https://i.loli.net/2017/11/10/5a05791f11d67.png)

    由于该用例调用了\*switchOnByDoorOpenSignalWithCheckWhenIgnOff这个case，程序会自动生成一个解析版的ini文件，将原ini中被调用的case展开，解析成其对应的测试函数步骤。

    \*switchOnByDoorOpenSignalWithCheckWhenIgnOff这个case对应的步骤如下图所示：

    ![](https://i.loli.net/2017/11/10/5a056183822b5.png)

    解析结果如下图所示：

    ![](https://i.loli.net/2017/11/10/5a057a156a4f3.png)

    程序除了生成相应的ini文件外，还会自动生成对应的.can文件，将这部分文件导入vTESTstudio才能最终在vTESTstudio中生成相应的测试序列。生成的.can文件的对应部分如下所示：

    ![](https://i.loli.net/2017/11/10/5a057b2657a00.png)

    首先说明，事实上，所有ini文件上的step其实对应了一个routeNum数组。默认情况下，该routeNum数组的所有元素均为0，即选择路径标识为0，即第一个路径。因为默认情况下是不存在带|号的function，所以仅有唯一的路径。但是，当带|号的function被引入之后，我们就必须对routeNum数组中的相应元素进行设置。这其中基本的对应关系是，step1对应了routeNum[0]，step2对应了routeNum[1]，以此类推……至于数组元素的取值，0代表第一条路径，1代表第二条路径，2代表第三条路径，以此类推。

    那么我们回过头来看解析版的ini，可以发现，带|号的function被引入进了从step7开始至step11终止的这5个step，因此需要特殊配置的routeNum数组中的相应元素就是[7]至[11]。

    由于此处的实际情形是只有3条路径，并且这3条路径分别对应了step8-12共同的第1路径，第2路径和第3路径，那么该程序可以被简化。

    手工将.can文件这部分修改如下：

    ![](https://i.loli.net/2017/11/10/5a057d62022bc.png)

    最终当用户使用vTESTstudio来调用这个case的时候，就可以通过vTESTstudio右侧自带的parameter Values面板，将包括stepRouteNum在内的相应的各实参可能的取值填入，然后由Combinatorics一栏来决定这四个参数间的数值匹配方式。以下是针对上例的最终配置结果：

    ![](https://i.loli.net/2017/11/10/5a057f035c5fa.png)

    需要注意的是，符号|的用法，仅针对函数，而不针对于首字符带\*的section。

###_testStepCfgEditor的生成文档说明

_testStepCfgEditor应用程序在正常运行结束后，会生成3个文档。

1. _testStepCfg.ini

    该文档是运行testStepCfgEditor程序时，首先要求导入的文档。_testStepCfg.ini是推荐输入的文件名，目的是为了与后续生成的testStepCfg.ini文件区别开来。当然你也可以选择其他的文件名。

    ![](https://i.loli.net/2017/09/26/59c9efe564d32.png)

    导入后，你可以进行相应的修改，新增或者删除等操作，可以使用之前声明的特殊格式来实现特殊的目的。

    这份文档其实是最好的保存整个测试逻辑思路的文件。

    当所需数据内容全部添加完成后，点击面板右上角的一个钢笔形状的图标（图标上方标注有Generate testStepCfg.ini）实现最终文件生成，这时候会根据之前在应用程序表格中的相应内容，自动更新覆盖之前导入的文本（文件名保持不变）。

2. testStepCfg.ini

    该文档是运行testStepCfgEditor程序，当用户点击生成按钮时，最终生成的一个解析版本的ini文件，并且文件名固定为testStepCfg.ini。

    生成解析版ini文件的目的，是将之前_testStepCfg.ini中涉及到的调用首字符为\*的section这部分，替换为其section自身的序列内容。vTESTstudio中的库函数，最终调用的，其实是解析版的这个ini文件。

    以下是\_testStepCfg.ini和testStepCfg.ini两份文档的一个对比图，从中可以看出testStepCfg.ini这份文档中，已经不存在任何首字符为\*的section了，它们的内容已经被展开代入到\_testStepCfg.ini中相应的调用位置。

    ![](https://i.loli.net/2017/11/10/5a05804532491.png)

3. basicFunctionTest.can

    该文档也是当用户点击生成按钮时，自动生成的。basicFunctionTest.can是一个推荐的文件名，用户可以根据具体的需求对名字进行相应的更改。

    该文件的目的，是让用户导入vTESTstudio后，能够调用之前生成的testStepCfg.ini文件中各个section的函数序列来生成相应的test case。

    以下阐述basicFunctionTest.can与testStepCfg.ini之间具体的对应关系。
    
    - 针对section中不含带\*号的实参，不含带|号的function的情况

        这是最简单的情况，只需要调用stateMachine函数，并指明section name，后面两个参数默认为routeNum和noParaPick即可。因为默认情况下，routeNum每个元素都为0，意即选择第一条路径。noParaPick则意味着不含任何带\*号的实参。

        testcase的名字，也被设置成与section name相同。这样在对照ini文本的时候，不至于混淆。

        以下是一个例子的图示：

        ![](https://i.loli.net/2017/09/26/59ca04b283267.png)

    - 针对section中含带\*号的实参，不含带|号的function的情况

        这种情况下，调用stateMachine函数时，除了指明section name，还需要设定相应的paraPick数组。

        下面来看一个例子：

        解析版ini文件中，chkDrivingModeReqSigImpWhenIgnOff这个section包含有3个带*号的实参。这种情况下，需要专门设定相应数组paraPick，将实参名与同名字符串变量挂钩。

        ![](https://i.loli.net/2017/11/10/5a05824e7d0ed.png)

        最终通过vTESTstudio中的parameter values面板给同名字符串变量赋值，用例运行时，程序会自动采集同名字符串变量的赋值来运作相应的函数。

        ![](https://i.loli.net/2017/11/10/5a05856e5c5e1.png)

    - 针对section中含带\*号的实参，含带|号的function的情况

        这是最复杂的一种情况，在调用stateMachine函数时，除了指明section name，设定相应的paraPick数组，还需要设定routeNum数组。

        下面我们来看一个之前的例子，把之前这个案例再总结一下。

        ![](https://ooo.0o0.ooo/2017/11/13/5a08f16ba8a45.png)

        首先，解析版ini的step序号和routeNum元素编号的对应关系是，step1对应routeNum[0]，step2对应routeNum[1]，以此类推.

        其次，routeNum数组元素的取值和路径的对应关系，举图中step8这一行为例来说明。step8对应routeNum[7]，routeNum[7]取值为0，则取路径1，即step8选择操作函数为`signalSetting,RKEDoorLockCmd,1,1`；routeNum[7]取值为1，则取路径2，即step7选择操作函数为`wait,23000`；routeNum[7]取值为2，则取路径3，即step7选择操作函数为`vtSysPwrSupVoltSet,supint->out2,0`。

        再次，程序为了方便起见，给带|号的function的每一个step都分别设定了一个stepRouteNum变量，譬如routeNum[7]设定了一个stepRouteNum7的变量，routeNum[8]设定了一个stepRouteNum8的变量，以此类推。因为理论上，每一个routeNum都可以独立选取各自路径，但是事实上，不同的情况下可能会有不同的限制。譬如该例中，唯有当routeNum[7]到routeNum[11]这5个step的路径选取保持一致的时候，才符合需求文档的意义。那么这个时候，我们就可以将stepRouteNum7到stepRouteNum11这5个变量用同一个变量stepRouteNum来替换，这样变量的数量就可以大幅减少，这样parameter values面板的设定就会简易很多。

        不过这部分工作需要用户自己手动完成，因为程序不可能事先预知你对routeNum的限定条件。

        手工将.can文件这部分修改如下：

        ![](https://i.loli.net/2017/11/10/5a057d62022bc.png)

        以下是针对上例的最终取值结果：

        ![](https://i.loli.net/2017/11/10/5a057f035c5fa.png)
        
###函数功能介绍

- 用户界面操作类函数

    1. testValidateTesterConfirmation
   
        函数原型： long TestValidateTesterConfirmation(char question[])

        功能： 弹出提示窗口，指示操作人员下一步的操作动作。

        参数：

        - question： 弹出窗口上显示的字符串内容。

        函数返回值： 

        - 3: The tester clicked Unclear；
        - 2： The tester clicked No；
        - 1： The tester clicked Yes；
        - 0： Timeout occurred；
        - -1001: General error, e.g. due to a call outside of a test sequence.；
        - -1002: Constraint occurred.
        <br></br>

- 通讯协议类函数

    1. signalSetting
    
        函数原型： void signalSetting (char sigName[], float valueBase,int range) 

        功能： 给特定信号赋特定范围内的一个随机数。这个数的值为valueBase加上一个随机整数，0 ≤ 随机整数 < range。 

        参数：

        - sigName： 赋值信号在database上的名称。
        - valueBase： 赋值的基值
        - range： 赋值在基值上的随机整数范围偏差为0 — range-1

        函数返回值：

        - 0： 信号设置成功；
        - -1001: 该名称的信号不存在；
        - -1002: 5s内信号未被设定为指定值。
<br></br>
    2. signalContSetting
   
        函数原型： void signalContSetting (char settingSignal[], float startVal, int range, long msGapTime)

        功能： 让特定信号从初始值startVal开始连续自增，增幅为1，一直自增到startVal+range-1为止。其中，每次赋值指令发出后，会在检测信号赋值成功后，再等待msGapTime毫秒间隔，发送下一条赋值指令。

        参数：

        - sigName： 赋值信号在database上的名称。
        - startVal： 赋值的初值。
        - range： 赋值的增长范围。
        - msGapTime： 赋值的间隔时间（ms）。

        函数返回值： 

        - 0： 信号设置成功；
        - -1001: 该名称的信号不存在；
        - -1002: 5s内信号未被设定为指定值；
        - -1003: General error, for example, TestWaitForTimeout functionality is not available；
        - -1004: Resume due to constraint violation in function:testWaitForTimeout；
        - -1005: 输入的msGapTime值为负数。
<br></br>
    3. testEnableMsg
   
        函数原型： long TestEnableMsg (char aMessageName[])

        功能： 在使用TestDisableMsg函数屏蔽某周期性消息后，利用这条指令，可以重新激活该消息的发送。**注：该函数仅适用于由database定义的周期性消息。**

        参数：

        - aMessageName： 重新激活发送的周期性消息名称。

        函数返回值：

        - 0： No error;
        - -1001: General error，譬如，该消息不存在。
<br></br>
    4. testDisableMsg
   
        函数原型： long TestDisableMsg (char aMessageName[])

        功能： 屏蔽数据库中的某周期性消息的发送。**注：该函数仅适用于由database定义的周期性消息。**

        参数：

        - aMessageName： 屏蔽的周期性消息名称。

        函数返回值：

        - 0： No error；
        - -1001: General error，譬如，该消息不存在。
<br></br>
    5. linActivateSlot
   
        函数原型： long linActivateSlot(int tableIndex, int slotIndex)

        功能： 在使用linDeactivateSlot函数屏蔽某LIN消息后，利用这条指令，可以重新根据该消息在LDF文件中调度表的位置（tableIndex, slotIndex），来激活该消息的发送。

        参数：

        - tableIndex： 查看LDF文件，获取其在调度表中的tableIndex。该Index是从0开始的整数；
        - slotIndex： 查看LDF文件，获取其在调度表中的slotIndex。该Index是从0开始的整数。

            关于这两个参数的取值，打开LDF文件，参考下图的标注自然就清楚了。需要注意的是，如果你想激活下图中所示的消息BCM1\_LIN1\_01，那么请激活所有和BCM1\_LIN1\_01相关的tableIndex和slotIndex，以保证消息发送的频率和LDF的定义是一致的。

            ![](https://s1.ax1x.com/2017/11/29/hXhrD.png)

        函数返回值：

        - -1001： 激活发送失败；
        - 非0正值: 激活发送成功。
<br></br>
    6. linDeactivateSlot
   
        函数原型： long linDeactivateSlot(dword tableIndex, dword slotIndex)

        功能： 根据某LIN消息在LDF文件中调度表的位置（tableIndex, slotIndex），屏蔽该消息的发送。

        参数：

        - tableIndex： 查看LDF文件，获取其在调度表中的tableIndex。该Index是从0开始的整数；
        - slotIndex： 查看LDF文件，获取其在调度表中的slotIndex。该Index是从0开始的整数。
        
            关于这两个参数的取值，打开LDF文件，参考下图的标注自然就清楚了。需要注意的是，如果你想屏蔽下图中所示的消息BCM1\_LIN1\_01，那么你需要屏蔽所有和BCM1\_LIN1\_01相关的tableIndex和slotIndex。

            ![](https://s1.ax1x.com/2017/11/29/hXhrD.png)

        函数返回值：

        - -1001： 屏蔽失败；
        - 非0正值: 屏蔽成功。
<br></br>
    7. sendCanUdsDiagChkResp
   
        函数原型： int sendCanUdsDiagChkResp (char serviceName[]) 

        功能： 指示上位机发送某条特定的UDS CAN诊断消息，并检测产品发出的反馈消息是否正确。

        参数：

        - serviceName： paraCfg.ini中section：UDS Services下某个key的key name。

        函数返回值：

        - 非零正值： 消息发送成功，反馈消息正确，返回接收消息的字节位的取值（byte）。
        - -1001： 输入的section或者key name不正确，无法在paraCfg.ini的section：UDS Services下找到相应的key；
        - -1002： 上位机发送诊断消息失败；
        - -1003： 测试系统未检测到符合paraCfg.ini中相应位置下的配置参数recMsgId的反馈消息；
        - -1004： paraCfg.ini中相应位置下的配置参数offsetByteChkPos及chkByteLen的值输入错误，和大于8，无法检测相应的字节内容是否正确；
        - -10001： 产品反馈消息中的检测部分字节内容与paraCfg.ini中相应位置下的配置参数chkRecMsgPartData不符。
<br></br>
    8. sendCanKostiaDiagChkResp
   
        函数原型： int sendCanKostiaDiagChkResp (char serviceName[])

        功能： 指示上位机发送某条特定的Kostia CAN诊断消息，并检测产品发出的反馈消息是否正确。

        参数：

        - serviceName： paraCfg.ini中section：Kostia Services下某个key的key name。

        函数返回值：

        - 7： 消息发送成功，反馈消息正确，返回接收消息的有效字节长度（byte）。Kostia消息的有效字节长度为7；
        - -1001： 输入的section或者key name不正确，无法在paraCfg.ini的section：Kostia Services下找到相应的key；
        - -1002： 上位机发送诊断消息失败；
        - -1003： 测试系统未检测到符合paraCfg.ini中相应位置下的配置参数recMsgId的反馈消息；
        - -1004： paraCfg.ini中相应位置下的配置参数offsetByteChkPos及chkByteLen的值输入错误，和大于8，无法检测相应的字节内容是否正确；
        - -10001： 产品反馈消息中的检测部分字节内容与paraCfg.ini中相应位置下的配置参数chkRecMsgPartData不符。
<br></br>
    9. sendLinUdsDiagChkResp
   
        函数原型： int sendLinUdsDiagChkResp (char serviceName[])

        功能： 指示上位机发送某条特定的UDS LIN诊断消息，并检测产品发出的反馈消息是否正确。

        参数：

        - serviceName： paraCfg.ini中section：UDS Services下某个key的key name。

        函数返回值：

        - 非零正值： 消息发送成功，反馈消息正确，返回接收消息的字节位的取值（byte）；
        - -1001： 输入的section或者key name不正确，无法在paraCfg.ini的section：UDS Services下找到相应的key；
        - -1002： 上位机发送诊断消息失败；
        - -1003： 5s内测试系统未检测到符合paraCfg.ini中相应位置下的配置参数recMsgId的反馈消息；
        - -1004： paraCfg.ini中相应位置下的配置参数 offsetByteChkPos及chkByteLen的值输入错误，和大于8，无法检测相应的字节内容是否正确；
        - -10001： 产品反馈消息中的检测部分字节内容与paraCfg.ini中相应位置下的配置参数chkRecMsgPartData不符。
<br></br>
    10. sendLinKostiaDiagChkResp
   
        函数原型： int sendLinKostiaDiagChkResp (char serviceName[])

        功能： 指示上位机发送某条特定的Kostia LIN诊断消息，并检测产品发出的反馈消息是否正确。

        参数：

        - serviceName： paraCfg.ini中section：Kostia Services下某个key的key name。

        函数返回值：

        - 7： 消息发送成功，反馈消息正确，返回接收消息的有效字节长度（byte）。Kostia消息的有效字节长度为7；
        - -1001： 输入的section或者key name不正确，无法在paraCfg.ini的section：Kostia Services下找到相应的key；
        - -1002： 上位机发送诊断消息失败；
        - -1003： 5s内测试系统未检测到符合paraCfg.ini中相应位置下的配置参数recMsgId的反馈消息；
        - -1004： paraCfg.ini中相应位置下的配置参数offsetByteChkPos及chkByteLen的值输入错误，和大于8，无法检测相应的字节内容是否正确；
        - -10001： 产品反馈消息中的检测部分字节内容与paraCfg.ini中相应位置下的配置参数chkRecMsgPartData不符。
<br></br>
    11. decodeAsciiFromRecDiag
   
        函数原型： void decodeAsciiFromRecDiag (int offsetBytePos,int chkByteLen,char decodeItem[]) 

        功能： 按照Ascii方式解析接收到的最新的一条产品反馈的LIN或CAN消息。

        参数：

        - offsetBytePos： 针对sendCanUdsDiagChkResp，sendCanKostiaDiagChkResp，sendLinUdsDiagChkResp，sendLinKostiaDiagChkResp这四个函数的返回消息的有效字节内容，定义的为解析而截取的起始字节位（第一个字节的offsetBytePos=0）。注：针对sendCanUdsDiagChkResp，sendLinUdsDiagChkResp这两个函数，有效字节内容就是接收到返回UDS message字节长度位之后的所有字节（如果有续帧的话，则将续帧标识相关的字节剔除）；针对sendCanKostiaDiagChkResp，sendLinKostiaDiagChkResp这两个函数，有效字节内容就是接收到返回Kostia message的Function title字节位之后的所有字节；
        - chkByteLen： 为解析而截取的字节长度；
        - decodeItem： 报告中显示的解析项名称。

        函数返回值：

        - 0： ASCII码转换成功；
        - -1001： 输入的section或者key name不正确，无法在paraCfg.ini中找到相应的key；
        - -1002： 上位机发送诊断消息失败；
        - -1003： 5s内测试系统未检测到符合paraCfg.ini中相应位置下的配置参数recMsgId的反馈消息；
        - -1004： paraCfg.ini中相应位置下的配置参数offsetByteChkPos及chkByteLen的值输入错误，和大于8，无法检测相应的字节内容是否正确；
        - -1005： 为进行转码而配置的offsetByteChkPos及chkByteLen的值输入错误，二者之和大于之前接收到消息的有效字节长度，造成无法正确截取字节内容，进行ASCII码转换失败；
        - -10001： 产品反馈消息中的检测部分字节内容与paraCfg.ini中相应位置下的配置参数chkRecMsgPartData不符。
<br></br>
- General类函数

    1. wait

        函数原型： void wait (int waitMs)

        功能： 等待一定时间（ms）。

        参数：

        - waitMs： 设置等待时间（ms），当值为0时，可作为空函数（NOP）使用。

        函数返回值：

        - 0： Resume due to timeout；
        - -1001： General error, for example, testWaitForTimeout functionality is not available；
        - -1002： Resume due to constraint violation in function:testWaitForTimeout；
        - -1003： 输入的waitMs值为负数。
<br></br>    
- vtSystem操作类函数

    1. vtSysPwrSupInit

        函数原型： void vtSysPwrSupInit (char pwrConnectWay[]) 

        功能： 根据paraCfg.ini中section：vt7001Cfg下某个key的配置内容，初始化vtSystem中vt7001板卡，电源供应来自于vt7001板卡内部电源。

        参数：

        - pwrConnectWay： paraCfg.ini中section：vt7001Cfg下某个key的key name。

        函数返回值：

        - 0： vt7001板卡内部电源模式配置初始化成功；
        - -1001： paraCfg.ini中section:vt7001Cfg对应key下的key value数目不等于3；
        - -1002： paraCfg.ini中section:vt7001Cfg对应key下的interConnectionMode不等于0（0=Internal Power Supply only），outChNum不等于1或2；
        - -1003： Call function:vtsSetInterconnectionMode or vtsSetRefVoltageMode error；
        - -1004： The namespace on which the command was called does not exist or is not a valid VT System namespace；
        - -1005： The specified mode is not valid；
        - -1006： The function vtsSetInterconnectionMode or vtsSetRefVoltageMode wasn't called in the context of the main method of a test module. So it is not possible to wait until the setting will be taken over from the VT System. Otherwise the call was successful but it is not sure if the settings have been taken over already when the call returns；
        - -1007： name space was not found or second try to define the same name space;
        - -1008： variable was not found or second try to define the same variable;
        - -1009： no writing right for the name space available;
        - -1010： the variable has no suitable type for the function:SysSetVariableInt.
<br></br>
    2. vtSysWithExPwrSupInit

        函数原型： void vtSysWithExPwrSupInit (char pwrConnectWay[])

        功能： 根据paraCfg.ini中section：vt7001Cfg下某个key的配置内容，初始化vtSystem中vt7001板卡，电源供应来自于vt7001的外接电源。

        参数：

        - pwrConnectWay： paraCfg.ini中section：vt7001Cfg下某个key的key name。

        函数返回值：

        - 0： vt7001板卡外部电源模式配置初始化成功；
        - -1001： paraCfg.ini中section:vt7001Cfg对应key下的key value数目不等于3；
        - -1002： paraCfg.ini中section:vt7001Cfg对应key下的interConnectionMode不等于1或2（1=Power Supply 1 only，2=Power Supply 2 only），outChNum不等于1或2；
        - -1003： Call function:vtsSetInterconnectionMode or vtsSetRefVoltageMode or vtsSetMaxCurrentMode error；
        - -1004： The namespace on which the command was called does not exist or is not a valid VT System namespace；
        - -1005： The specified mode is not valid；
        - -1006： The function vtsSetInterconnectionMode or vtsSetRefVoltageMode or vtsSetMaxCurrentMode wasn't called in the context of the main method of a test module. So it is not possible to wait until the setting will be taken over from the VT System. Otherwise the call was successful but it is not sure if the settings have been taken over already when the call returns；
        - -1007： name space was not found or second try to define the same name space;
        - -1008： variable was not found or second try to define the same variable;
        - -1009： no writing right for the name space available;
        - -1010： the variable has no suitable type for the function:SysSetVariableInt.
<br></br>
    3. vtSysPwrSupVoltSet

        函数原型： void vtSysPwrSupVoltSet (char pwrConnectWay[], float volt)

        功能： 在之前电源供应配置为vt7001内部的前提下，设置电源电压值。

        参数：

        - pwrConnectWay： 与vtSysPwrSupInit中的此参数值相同。
        - volt： 电源电压值。

        函数返回值：

        - 0： vt7001板卡内部电源模式电压设置成功；
        - -1001： paraCfg.ini中section:vt7001Cfg对应key下的key value数目不等于3；
        - -1002： name space was not found or second try to define the same name space；
        - -1003： variable was not found or second try to define the same variable；
        - -1004： no writing right for the name space available；
        - -1005： the variable has no suitable type for the function：sysSetVariableFloat.
<br></br>
    4. vtSysExPwrSupSet

        函数原型： void vtSysExPwrSupSet (char pwrConnectWay[], float volt, float maxI, int k) 

        功能： 在之前电源供应配置为vt7001外接电源的前提下，设置电源电压值。

        参数：

        - pwrConnectWay： 与vtSysWithExPwrSupInit中的此参数值相同；
        - volt： 电源电压值；
        - maxI： 电源可供最大电流值；
        - k： 等于vt7001外接电源的输出电压与vt7001输出对外接电源的控制电压的比值，也是vt7001外接电源的输出最大电流与vt7001输出对外接电源的最大控制电流的比值。对于现今实验室中使用的外接电源SYSKON P4500而言，k=12.

        函数返回值：

        - 0： vt7001板卡外部电源模式电压设置成功；
        - -1001： paraCfg.ini中section:vt7001Cfg对应key下的key value数目不等于3；
        - -1002： paraCfg.ini中section:vt7001Cfg对应key下的interConnectionMode不等于1或2（1=Power Supply 1 only，2=Power Supply 2 only），outChNum不等于1或2；
        - -1003： name space was not found or second try to define the same name space；
        - -1004： variable was not found or second try to define the same variable；
        - -1005： no writing right for the name space available；
        - -1006： the variable has no suitable type for the function：sysSetVariableFloat.
<br></br>
    5. vtSysPwrSupVoltGet

        函数原型： float vtSysPwrSupVoltGet (char pwrConnectWay[], float highLimitV, float lowLimitV) 

        功能： 测量vt7001板卡的输出电压。

        参数：

        - pwrConnectWay： 与之前vtSysPwrSupInit或vtSysWithExPwrSupInit中的此参数值相同；
        - highLimitV： 允许的输出电压的最大值，单位V；
        - lowLimitV： 允许的输出电压的最小值，单位V；

        函数返回值：

        - 0： vt7001板卡电源电压读取成功，且在paraCfg.ini配置文件指定的范围；
        - -1001： paraCfg.ini中section:vt7001Cfg对应key下的key value数目不等于3；
        - -10001： 电压值超过paraCfg.ini配置文件指定的范围。
<br></br>
    6. vtSysPwrSupCurrGet

        函数原型： float vtSysPwrSupCurrGet (char pwrConnectWay[],float highLimitA,float lowLimitA,enum vt7001MeasureRange vt7001MeasureRange,enum currentUnit currentUnit) 

        功能： 测量vt7001板卡的输出电流。

        参数：

        - pwrConnectWay： 与之前vtSysPwrSupInit或vtSysWithExPwrSupInit中的此参数值相同；
        - highLimitA： 允许的输出电流的最大值，单位A；
        - lowLimitA： 允许的输出电流的最小值，单位A；
        - vt7001MeasureRange： 系统电流测量范围，参数意义如下：all = 0,\_100uA\_1mA = 1,\_1mA\_10mA = 2,\_10mA\_100mA = 3,\_100mA\_1A = 4,\_1A\_10A = 5,\_10A\_100A = 6
        - currentUnit： 报告中显示的测量结果单位设置，参数意义如下：uA = 0,mA = 1,A = 2

        函数返回值：

        - 0： vt7001板卡电源电流读取成功，且在paraCfg.ini配置文件指定的范围；
        - -1001： paraCfg.ini中section:vt7001Cfg对应key下的key value数目不等于3；
        - -1002： Call function:vtsSetMinCurrentMeasurementRange error；
        - -1003： The namespace on which the command was called does not exist or is not a valid VT system namespace；
        - -1005： The function vtsSetMinCurrentMeasurementRange wasn't called in the context of the main method of a test module. So it is not possible to wait until the setting will be taken over from the VT system. Otherwise the call was successful but it is not sure if the settings have been taken over already when the call returns；
        - -10001： 电流值超过paraCfg.ini配置文件指定的范围。
<br></br>    
    7. vtsSetThreshold1_8

        函数原型： long vtsSetThreshold1_8 (char moduleNum[],double Threshold)

        功能： 设置某张VT2516板卡1-8通道的高低电平间的阈值。阈值电平的高低也同样会影响到vtSystem对PWM波形的占空比和频率的测量结果。

        参数：

        - moduleNum： 需要设置阈值的VT2516板卡的模块号；
        - Threshold： 所需设定的阈值，范围为0-25V；

        函数返回值：

        - 0： 函数调用成功；
        - -1001： 函数调用错误；
        - -1002： 模块号设置错误，导致namespace无法被系统识别；
        - -1003： 指定的阈值超过允许范围；
        - -1004： The function wasn't called in the context of the main method of a test module.
<br></br>
    8. vtsSetThreshold9_16

        函数原型： long vtsSetThreshold9_16 (char moduleNum[],double Threshold)

        功能： 设置某张VT2516板卡9-16通道的高低电平间的阈值。阈值电平的高低也同样会影响到vtSystem对PWM波形的占空比和频率的测量结果。

        参数：

        - moduleNum： 需要设置阈值的VT2516板卡的模块号；
        - Threshold： 所需设定的阈值，范围为0-25V；

        函数返回值：

        - 0： 函数调用成功；
        - -1001： 函数调用错误；
        - -1002： 模块号设置错误，导致namespace无法被系统识别；
        - -1003： 指定的阈值超过允许范围；
        - -1004： The function wasn't called in the context of the main method of a test module.
<br></br>
    9. prodPwmOutChk

        函数原型： void prodPwmOutChk (char pinName[],float expectedFreq,float expectedDuty,int deviationRange)

        功能： 检测产品某个pin的输出PWM波形的频率与占空比，看是否在允许的偏差范围内。

        参数：

        - pinName： paraCfg.ini中section：vt2516Cfg下某个key的key name；
        - expectedFreq： 被检测的PWM波形应达到的频率(f)，允许的偏差范围为0.5%；
        - expectedDuty： 被检测的PWM波形应达到的占空比；
        - deviationRange： 被检测的PWM波形的占空比与expectedDuty间容许的正反偏差(%)。

        函数返回值：

        - 0： 成功检测到产品输出的PWM波形，且在paraCfg.ini配置文件指定的范围；
        - -1001： paraCfg.ini中section:vt2516Cfg对应key下的key value数目不等于2；
        - -10001： 产品输出的PWM波形不合格，不符合电压小于0.5V的单一低电平要求；
        - -10002： 产品输出的PWM波形不合格，不符合电压大于10V的单一高电平要求；
        - -10003： 产品输出的PWM波形不合格，PWM频率超过paraCfg.ini配置文件指定频率的0.5%；
        - -10004： 产品输出的PWM波形不合格，PWM占空比超过paraCfg.ini配置文件指定的偏差范围；
        - -10005： 产品输出的PWM波形不合格，PWM频率超过paraCfg.ini配置文件指定频率的0.5%，且PWM占空比超过paraCfg.ini配置文件指定的偏差范围。
<br></br>
    10. prodPwmOutRisingEdgeMeas

        函数原型： void prodPwmOutRisingEdgeMeas (char productPwmOutMode[])

        功能： 根据paraCfg.ini中section：pwmTimeCfg下某个key的配置内容，监控产品某个pin的输出PWM波形的占空比变化过程，测量占空比上升到最大值的时间等参数是否合乎配置要求。

        参数：

        - productPwmOutMode： paraCfg.ini中section：pwmTimeCfg下某个key的key name；
        
        函数返回值：

        - 0： 成功检测到产品输出的PWM波形占空比的上升时间，且在paraCfg.ini配置文件指定的范围；
        - -1001： paraCfg.ini中section:vt2516Cfg对应key下的key value数目不等于2；
        - -10001： 产品输出的PWM波形的占空比，在3s内都没有检测到上升的趋势；
        - -10002： 产品输出的PWM波形的占空比，在上升结束点检测开始5s后占空比仍然在继续上升；
        - -10005： 产品输出的PWM波形不合格，占空比上升时间超过paraCfg.ini配置文件指定的偏差范围。
<br></br>
    11. prodPwmOutKeepTimeMeas

        函数原型： void prodPwmOutKeepTimeMeas (char productPwmOutMode[])

        功能： 根据paraCfg.ini中section：pwmTimeCfg下某个key的配置内容，监控产品某个pin的输出PWM波形的占空比变化过程，测量占空比在上升结束后在稳定值维持的时间等参数是否合乎配置要求。

        参数：

        - productPwmOutMode： paraCfg.ini中section：pwmTimeCfg下某个key的key name；
        
        函数返回值：

        - 0： 成功检测到产品输出的PWM波形占空比的保持时间，且在paraCfg.ini配置文件指定的范围；
        - -1001： paraCfg.ini中section:vt2516Cfg对应key下的key value数目不等于2；
        - -10002： 产品输出的PWM波形的占空比，在上升结束点检测开始5s后占空比仍然在继续上升；
        - -10003： 产品输出的PWM波形的占空比，在1min内都没有检测到下降的趋势。
        - -10006： 产品输出的PWM波形不合格，占空比保持时间超过paraCfg.ini配置文件指定的偏差范围。
<br></br>
    12. prodPwmOutFallingEdgeMeas

        函数原型： void prodPwmOutFallingEdgeMeas (char productPwmOutMode[]) 

        功能： 根据paraCfg.ini中section：pwmTimeCfg下某个key的配置内容，监控产品某个pin的输出PWM波形的占空比变化过程，测量占空比从稳定值下降到某特定占空比的时间等参数是否合乎配置要求。

        参数：

        - productPwmOutMode： paraCfg.ini中section：pwmTimeCfg下某个key的key name；
        
        函数返回值：

        - 0： 成功检测到产品输出的PWM波形占空比的下降时间，且在paraCfg.ini配置文件指定的范围；
        - -1001： paraCfg.ini中section:vt2516Cfg对应key下的key value数目不等于2；
        - -10003： 产品输出的PWM波形的占空比，在1min内都没有检测到下降的趋势；
        - -10004： 产品输出的PWM波形的占空比，在下降结束点检测开始5s后占空比仍然在继续下降；
        - -10007： 产品输出的PWM波形不合格，占空比下降时间超过paraCfg.ini配置文件指定的偏差范围。
<br></br>
    13. prodPwmOutRiseFallCurveMeas

        函数原型： void prodPwmOutRiseFallCurveMeas (char productPwmOutMode[])

        功能： 根据paraCfg.ini中section：pwmTimeCfg下某个key的配置内容，监控产品某个pin的输出PWM波形的占空比变化过程，测量占空比从上升到最大值（上升到最大值后，立刻下降或稳定一段时间后再下降）再下降到某特定占空比的时间等参数是否合乎配置要求。

        参数：

        - productPwmOutMode： paraCfg.ini中section：pwmTimeCfg下某个key的key name；
        
        函数返回值：

        - 0： 成功检测到产品输出的PWM波形占空比的上升下降时间，且在paraCfg.ini配置文件指定的范围；
        - -1001： paraCfg.ini中section:vt2516Cfg对应key下的key value数目不等于2；
        - -10001： 产品输出的PWM波形的占空比，在3s内都没有检测到上升的趋势；
        - -10002： 产品输出的PWM波形的占空比，在上升结束点检测开始5s后占空比仍然在继续上升；
        - -10003： 产品输出的PWM波形的占空比，在1min内都没有检测到下降的趋势；
        - -10004： 产品输出的PWM波形的占空比，在下降结束点检测开始5s后占空比仍然在继续下降；
        - -10005： 产品输出的PWM波形不合格，占空比上升时间超过paraCfg.ini配置文件指定的偏差范围；
        - -10007： 产品输出的PWM波形不合格，占空比下降时间超过paraCfg.ini配置文件指定的偏差范围；
        - -10008： 产品输出的PWM波形不合格，占空比上升时间超过paraCfg.ini配置文件指定的偏差范围，且占空比下降时间超过paraCfg.ini配置文件指定的偏差范围。
<br></br>
    14. chFixVoltDOSet

        函数原型： void chFixVoltDOSet (char pinName[],enum digitalLevel level) 

        功能： 设置VT2516板卡的某通道接电源，接地或悬空。

        参数：

        - pinName： paraCfg.ini中section：vt2516Cfg下某个key的key name；
        - level： 接入电平的级别，参数意义如下：Low = 0,表示接地； High = 1,表示接电源； Floating = 2，表示悬空。
        
        函数返回值：

        - 0： VT2516板卡的通道电平状态设置成功；
        - -1001： paraCfg.ini中section:vt2516Cfg对应key下的key value数目不等于2；
        - -1002： name space was not found or second try to define the same name space；
        - -1003： variable was not found or second try to define the same variable；
        - -1004： no writing right for the name space available；
        - -1005： the variable has no suitable type for the function：sysSetVariableInt；
        - -1006： General error, for example, functionality is not available；
        - -1007： Resume due to constraint violation；
        - -1008： 输入未知的电平状态。
<br></br>
    15. chAOSet

        函数原型： void chAOSet (char pinName[],float analogValue) 

        功能： 设置VT2516板卡的某通道的输出模拟电压大小。

        参数：

        - pinName： paraCfg.ini中section：vt2516Cfg下某个key的key name；
        - analogValue： 输出的模拟电压值。
        
        函数返回值：

        - 0： VT2516板卡的通道输出电压设置成功；
        - -1001： paraCfg.ini中section:vt2516Cfg对应key下的key value数目不等于2；
        - -1002： Call function:vtsSetStimulationMode or vtsSetCurveType or vtsSetPWMVoltageHigh or vtsSetStimulationMode error；
        - -1003： The namespace on which the command was called does not exist or is not a valid VT System namespace；
        - -1004： The specified mode is not valid；
        - -1005： The function vtsSetStimulationMode or vtsSetCurveType or vtsSetPWMVoltageHigh or vtsSetStimulationMode wasn't called in the context of the main method of a test module. So it is not possible to wait until the setting will be taken over from the VT System. Otherwise the call was successful but it is not sure if the settings have been taken over already when the call returns；
        - -1006： name space was not found or second try to define the same name space；
        - -1007： variable was not found or second try to define the same variable；
        - -1008： no writing right for the name space available；
        - -1009： the variable has no suitable type for the function：SysSetVariableInt。
<br></br>
    16. chRamVoltDOSet

        函数原型： void chRamVoltDOSet (char pinName[],enum prodInputStat state)  

        功能： 根据paraCfg.ini中section：vLevelCfg下某个key的配置内容，设置VT2516板卡的某通道的输出符合产品某pin脚active或inactive状态范围内的一个随机模拟电压值。

        参数：

        - pinName： paraCfg.ini中section：vLevelCfg下某个key的key name；
        - state： 设置产品pin所需达到的状态，参数意义如下：Inactive = 0； Active = 1。
        
        函数返回值： 

        - 0： VT2516板卡的通道电平状态设置成功；
        - -1001： paraCfg.ini中section:vLevelCfg对应key下的key value数目不等于4或section:vt2516Cfg对应key下的key value数目不等于2；
        - -1002： Call function:vtsSetStimulationMode or vtsSetCurveType or vtsSetPWMVoltageHigh or vtsSetStimulationMode error；
        - -1003： The namespace on which the command was called does not exist or is not a valid VT System namespace；
        - -1004： The specified mode is not valid；
        - -1005： The function vtsSetStimulationMode or vtsSetCurveType or vtsSetPWMVoltageHigh or vtsSetStimulationMode wasn't called in the context of the main method of a test module. So it is not possible to wait until the setting will be taken over from the VT System. Otherwise the call was successful but it is not sure if the settings have been taken over already when the call returns.；
        - -1006： name space was not found or second try to define the same name space；
        - -1007： variable was not found or second try to define the same variable；
        - -1008： no writing right for the name space available；
        - -1009： the variable has no suitable type for the function：SysSetVariableInt。
<br></br>
    17. prodDIPinStatGet

        函数原型： int prodDIPinStatGet (char pinName[])  

        功能： 根据paraCfg.ini中section：vLevelCfg下某个key的配置内容，来判定与VT2516板卡的某通道相连的产品某pin脚究竟是处于Inactive还是Active状态。

        参数：

        - pinName： paraCfg.ini中section：vt2516Cfg和vLevelCfg下某个共同的key的key name。
        
        函数返回值：

        - 1： Active；
        - 0： Inactive；
        - -1001： paraCfg.ini中section:vLevelCfg对应key下的key value数目不等于4或section:vt2516Cfg对应key下的key value数目不等于2；
        - -1002： 此pin脚的电平处于active和inactive之外的一个未定义状态。

        注：启用该函数前，针对填入的实参pinName值，需要预先开启对该pin对应的VT2516通道的电压测量功能。

        首先，在CANoe菜单栏上选择Configuration下的I/O Hardware，然后点击其下的VT System…

        ![](https://s1.ax1x.com/2017/11/28/hdFwq.png)
 
        在随后打开的VT System Configuration界面中，选中左侧相应板卡的通道，然后勾选右侧的Avg功能，即可开启该通道的电压测量功能。

        ![](https://s1.ax1x.com/2017/11/28/hdplQ.png)

    18. chPwmOutSet

        函数原型： void chPwmOutSet (char pinName[],char productPwmInMode[])

        功能： 根据paraCfg.ini中section：pwmWaveCfg下某个key的配置内容，让VT2516板卡的某通道输出特定的PWM波形提供给产品某特定pin脚。

        参数：

        - pinName： paraCfg.ini中section：vt2516Cfg下某个key的key name；
        - productPwmInMode： paraCfg.ini中section：pwmWaveCfg下某个key的key name。
        
        函数返回值：

        - 0： VT2516板卡输出PWM波形成功；
        - -1001： paraCfg.ini中section:vt2516Cfg对应key下的key value数目不等于2或section:pwmWaveCfg对应key下的key value数目不等于5；
        - -1002： Call function:vtsSetStimulationMode or vtsSetPWMVoltageLow or vtsSetPWMVoltageHigh or vtsSetCurveType or vtsStartStimulation error；
        - -1003： The namespace on which the command was called does not exist or is not a valid VT System namespace；
        - -1004： The specified mode is not valid；
        - -1005： The function vtsSetStimulationMode or vtsSetPWMVoltageLow or vtsSetPWMVoltageHigh or vtsSetCurveType or vtsStartStimulation wasn't called in the context of the main method of a test module. So it is not possible to wait until the setting will be taken over from the VT System. Otherwise the call was successful but it is not sure if the settings have been taken over already when the call returns；
        - -1006： name space was not found or second try to define the same name space；
        - -1007： variable was not found or second try to define the same variable；
        - -1008： no writing right for the name space available；
        - -1009： the variable has no suitable type for the function：sysSetVariableFloat。
<br></br>
    19. chLoadConnectStatSet

        函数原型： void chLoadConnectStatSet (char pinName[],enum connectStat stat)

        功能： 控制下图红笔圈出位置的开关，设置VT2516板卡的特定通道与original load/sensor的连接状态。

        ![](https://i.loli.net/2017/11/08/5a027d80977af.png)

        参数：

        - pinName： paraCfg.ini中section：vt2516Cfg下某个key的key name；
        - stat： 通道与original load/sensor的连接状态，参数意义如下：disconnect = 0； connect = 1。
        
        函数返回值：

        - 0： VT2516板卡通道的负载连接状态设置成功；
        - -1001： paraCfg.ini中section:vt2516Cfg对应key下的key value数目不等于2；
        - -1002： name space was not found or second try to define the same name space；
        - -1003： variable was not found or second try to define the same variable；
        - -1004： no writing right for the name space available；
        - -1005： the variable has no suitable type for the function：sysSetVariableInt；
        - -1006： General error, for example, testWaitForTimeout functionality is not available；
        - -1007： Resume due to constraint violation in function:testWaitForTimeout。
<br></br>
- 产品操作及状态设置类函数

    1. prodOperWithPinStatImpOnSpecSigChk

        函数原型： void prodOperWithPinStatImpOnSpecSigChk (char operationMode[])

        功能： 根据paraCfg.ini中section：prodOperWithPinStatImpOnSpecSigCfg下某个key的配置内容，检测在产品某个特定pin脚处于某个状态的条件下，针对产品的某个操作动作对产品上某些信号的影响是否符合配置内容。

        参数：

        - operationMode： paraCfg.ini中section：prodOperWithPinStatImpOnSpecSigCfg下某个key的key name；
        
        函数返回值：

        - 0： paraCfg.ini中定义的产品的某个操作动作对产品上某些信号的影响符合配置内容；
        - -1001： 输入的section或者key name不正确，无法在paraCfg.ini的section：prodOperWithPinStatImpOnSpecSigCfg下找到相应的key；
        - -1002： paraCfg.ini中section:prodOperWithPinStatImpOnSpecSigCfg对应key下的数值数目减1后不能被5整除或paraCfg.ini中section:vLevelCfg对应key下的key value数目不等于4或section:vt2516Cfg对应key下的key value数目不等于2；
        - -1003： paraCfg.ini中定义的pin脚电平处于active和inactive之外的一个未定义状态；
        - -1004： General error, for example, testWaitForTimeout functionality is not available；
        - -1005： Resume due to constraint violation in function:testWaitForTimeout；
        - -10001： 某信号的值未按paraCfg.ini中的配置要求更新；
        - -10002： 某信号的值未按paraCfg.ini中的配置要求维持现状。
<br></br>
    2. prodOperWithPinStatImpOnSpecPwmChk

        函数原型： void prodOperWithPinStatImpOnSpecPwmChk (char operationMode[])

        功能： 根据paraCfg.ini中section：prodOperWithPinStatImpOnSpecPwmCfg下某个key的配置内容，检测在产品某个特定pin脚处于某个状态的条件下，针对产品的某个操作动作对产品的PWM输出波形的影响是否符合配置内容。

        参数：

        - operationMode： paraCfg.ini中section：prodOperWithPinStatImpOnSpecPwmCfg下某个key的key name；
        
        函数返回值：

        - 0： paraCfg.ini中定义的产品的某个操作动作对产品的PWM输出波形的影响符合配置内容；
        - -1001： 输入的section或者key name不正确，无法在paraCfg.ini的section：prodOperWithPinStatImpOnSpecPwmCfg下找到相应的key；
        - -1002： paraCfg.ini中section:prodOperWithPinStatImpOnSpecPwmCfg对应key下的数值数目减1后不能被6整除或paraCfg.ini中section:vLevelCfg对应key下的key value数目不等于4或section:vt2516Cfg对应key下的key value数目不等于2；
        - -1003： paraCfg.ini中定义的pin脚电平处于active和inactive之外的一个未定义状态；
        - -10001： 产品输出的PWM波形不合格，不符合电压小于0.5V的单一低电平要求；
        - -10002： 产品输出的PWM波形不合格，不符合电压大于10V的单一高电平要求；
        - -10003： 产品输出的PWM波形不合格，PWM频率超过paraCfg.ini配置文件指定频率的0.5%；
        - -10004： 产品输出的PWM波形不合格，PWM占空比超过paraCfg.ini配置文件指定的偏差范围；
        - -10005： 产品输出的PWM波形不合格，PWM频率超过paraCfg.ini配置文件指定频率的0.5%，且PWM占空比超过paraCfg.ini配置文件指定的偏差范围。
<br></br>
    3. prodOperWithSigStatImpOnSpecPwmChk

        函数原型： void prodOperWithSigStatImpOnSpecPwmChk (char operationMode[])

        功能： 根据paraCfg.ini中section：prodOperWithSigStatImpOnSpecPwmCfg下某个key的配置内容，检测在产品某个特定信号处于某个状态的条件下，针对产品的某个操作动作对产品的PWM输出波形的影响是否符合配置内容。

        参数：

        - operationMode： paraCfg.ini中section：prodOperWithSigStatImpOnSpecPwmCfg下某个key的key name；
        
        函数返回值：

        - 0： paraCfg.ini中定义的产品的某个操作动作对产品的PWM输出波形的影响符合配置内容；
        - -1001： 输入的section或者key name不正确，无法在paraCfg.ini的section：prodOperWithSigStatImpOnSpecPwmCfg下找到相应的key；
        - -1002： paraCfg.ini中section:prodOperWithSigStatImpOnSpecPwmCfg对应key下的数值数目减1后不能被6整除或section:vt2516Cfg对应key下的key value数目不等于2；
        - -1003： paraCfg.ini中定义的信号的取值不等于0也不等于1，即该信号不是一个二态的信号；
        - -10001： 产品输出的PWM波形不合格，不符合电压小于0.5V的单一低电平要求；
        - -10002： 产品输出的PWM波形不合格，不符合电压大于10V的单一高电平要求；
        - -10003： 产品输出的PWM波形不合格，PWM频率超过paraCfg.ini配置文件指定频率的0.5%；
        - -10004： 产品输出的PWM波形不合格，PWM占空比超过paraCfg.ini配置文件指定的偏差范围；
        - -10005： 产品输出的PWM波形不合格，PWM频率超过paraCfg.ini配置文件指定频率的0.5%，且PWM占空比超过paraCfg.ini配置文件指定的偏差范围。
<br></br>
    4. sigDirTwoStatInSet

        函数原型： void sigDirTwoStatInSet (char pinName[], enum determiningFactor dFct, enum prodInputStat state)

        功能： 根据paraCfg.ini中section：sigDirTwoStatInCfg下某个key的配置内容，决定是通过设置相应信号还是设置相应PIN的电平状态（信号有效的情况下，该状态优先由信号决定，忽略PIN的电平状态），来使产品进入某个二态中的一态。

        参数：

        - pinName： paraCfg.ini中section：sigDirTwoStatInCfg，vLevelCfg和vt2516Cfg下某个共同的key的key name；
        - dFct： 设置是由信号还是由硬线电平来决定产品的该状态，参数意义如下：determinedBySignal = 0，determinedByHardware = 1；
        - state： 设置产品需要达到二态中的哪一个状态，参数意义如下：Inactive = 0，Active = 1。
        
        函数返回值：

        - 0： 成功地设置产品进入某特定状态；
        - -1001： 输入的section或者key name不正确，无法在paraCfg.ini的section：sigDirTwoStatInCfg下找到相应的key；
        - -1002： General error；
        - -1003： 该名称的信号不存在；
        - -1004： 5s内信号未被设定为指定值。
        - -1005： paraCfg.ini中section:vLevelCfg对应key下的key value数目不等于4或section:vt2516Cfg对应key下的key value数目不等于2；
        - -1006： Call function:vtsSetStimulationMode or vtsSetCurveType or vtsSetPWMVoltageHigh or vtsSetStimulationMode error；
        - -1007： The namespace on which the command was called does not exist or is not a valid VT System namespace；
        - -1008： The specified mode is not valid；
        - -1009： The function vtsSetStimulationMode or vtsSetCurveType or vtsSetPWMVoltageHigh or vtsSetStimulationMode wasn't called in the context of the main method of a test module. So it is not possible to wait until the setting will be taken over from the VT System. Otherwise the call was successful but it is not sure if the settings have been taken over already when the call returns.；
        - -1010： name space was not found or second try to define the same name space；
        - -1011： variable was not found or second try to define the same variable；
        - -1012： no writing right for the name space available；
        - -1013： the variable has no suitable type for the function：SysSetVariableInt；
        - -1014： testWaitForTimeout functionality is not available；
        - -1015： Resume due to constraint violation in function:testWaitForTimeout。
<br></br>
    5. sigDirMulStatInSet

        函数原型： void sigDirMulStatInSet (char specStat[], enum determiningFactor dFct)

        功能： 根据paraCfg.ini中section：sigDirMulStatInCfg下某个key的配置内容，决定是通过设置相应信号还是设置相应PIN的PWM输入状态（信号有效的情况下，该状态优先由信号决定，忽略PIN的电平状态），来使产品进入某个多态中的一态。

        参数：

        - pinName： paraCfg.ini中section：sigDirMulStatInCfg下某个key的key name；
        - dFct： 设置是由信号还是由硬线电平来决定产品的该状态，参数意义如下：determinedBySignal = 0，determinedByHardware = 1。
        
        函数返回值：

        - 0： 成功地设置产品进入某特定状态；
        - -1001： 输入的section或者key name不正确，无法在paraCfg.ini的section：sigDirMulStatInCfg下找到相应的key；
        - -1002： General error；
        - -1003： 该名称的信号不存在；
        - -1004： 5s内信号未被设定为指定值；
        - -1005： paraCfg.ini中section:vt2516Cfg对应key下的key value数目不等于2或section:pwmWaveCfg对应key下的key value数目不等于5；
        - -1006： Call function:vtsSetStimulationMode or vtsSetPWMVoltageLow or vtsSetPWMVoltageHigh or vtsSetCurveType or vtsStartStimulation error；
        - -1007： The namespace on which the command was called does not exist or is not a valid VT System namespace；
        - -1008： The specified mode is not valid；
        - -1009： The function vtsSetStimulationMode or vtsSetPWMVoltageLow or vtsSetPWMVoltageHigh or vtsSetCurveType or vtsStartStimulation wasn't called in the context of the main method of a test module. So it is not possible to wait until the setting will be taken over from the VT System. Otherwise the call was successful but it is not sure if the settings have been taken over already when the call returns.；
        - -1010： name space was not found or second try to define the same name space；
        - -1011： variable was not found or second try to define the same variable；
        - -1012： no writing right for the name space available；
        - -1013： the variable has no suitable type for the function：sysSetVariableFloat。
<br></br>
    6. specStatImpOnSigChk

        函数原型： void specStatImpOnSigChk (char specStat[])

        功能： 根据paraCfg.ini中section：specStatImpactOnSigCfg下某个key的配置内容，检测产品进入某个状态后对相应信号的影响是否符合配置要求。

        参数：

        - specStat： paraCfg.ini中section：specStatImpactOnSigCfg下某个key的key name。
        
        函数返回值：

        - 0： 产品进入特定状态后对相应信号的影响符合配置要求；
        - -1001： 输入的section或者key name不正确，无法在paraCfg.ini的section：specStatImpactOnSigCfg下找到相应的key；
        - -1002： General error, for example, testWaitForTimeout functionality is not available；
        - -1003： Resume due to constraint violation in function:testWaitForTimeout；
        - -10001： paraCfg.ini中定义的信号没有在配置文档要求的时间之内更新为指定值。