###_testStepCfgEditor的使用说明

1. 确认工程中所有VI处于关闭状态，然后运行builder。注意，一定要保证工程中所有VI处于关闭状态，不然主VI运行会有异常，面板不能正常显示。

    ![](http://ww4.sinaimg.cn/large/0060lm7Tly1fjou772ps6j30bj0cct9b.jpg)

2. 点击弹出应用左上角的运行按钮，在菜单栏Editor选择testStepCfgEditor。

    ![](http://ww3.sinaimg.cn/large/0060lm7Tly1fjouad3yrtj304o051aa2.jpg)

3. 在随后弹出的窗口中可以选择加载已有的\_testStepCfg.ini文件进行后续的修改，或者可以在vTestStudioCfgEditor\cfg中新建空白的ini文件导入，从头制作一个新的\_testStepCfg.ini文件.注意，必须导入一个存在的文档，无论是否空白。选择完毕，点击确认键。

    ![](http://ww2.sinaimg.cn/large/0060lm7Tly1fjoudum6b9j317s0lw7a5.jpg)

4. 导入ini文件后，check一栏会显示相应的语法检测结果，如果出现数据类型不匹配或者数目不匹配或者符号格式等错误，check一栏会打上红色的×，并且会标注错误原因；检测正确的话，则会标注绿色的√。

    下图中同时包含有检测正确和错误的图示。需要注意的是，由于屏幕所限，每一列的宽度可能不足够展示该栏全部的信息，这个时候可以用鼠标双击你希望获得清楚信息的行，则该行每一栏的信息都会清晰地放大到上方的VIEW控件中。以下图为例，它展示的就是出错一行的每一栏的详细信息。

    ![](http://ww2.sinaimg.cn/large/0060lm7Tly1fjovfr0xk4j30zp0bd74w.jpg)

    
5. 修正之前内容的时候，如果需要在两行之间插入新的一行，或者删除某一行内容，可以将鼠标置于表格部分相应的行上，按右键，会弹出一个菜单，根据具体需求，在菜单中选择“在前面插入行”或“删除行”。注意，不要对列进行操作，如果不慎操作错误，请在菜单栏中选择exit退出，再重新启动应用程序，导入testStepCfgEditor。

    ![](http://ww1.sinaimg.cn/large/0060lm7Tly1fjovpt53bzj30es0dtmxg.jpg)

6. 在空白处填写新增内容，如果需要插入函数的话，先点击鼠标左键，将鼠标置于该行任一栏内，点击面板右侧的tree控件里具体的某个函数，这时候该函数和具体的参数说明就会被添加到该行相应的栏内。详情参考以下操作图例。

    ![](http://ww3.sinaimg.cn/large/0060lm7Tly1fjox5jbptcg312i0e4grh.gif)

7. 在空白处填写新增内容，填写完毕后，如果需要查看该行check一栏的判定结果，只需将鼠标点击到除此行以外的其他任意行上，就能立刻看到该行check栏上的判定结果。如果需要查看该行的详细信息，只需鼠标左键双击该行，就可以在上部view控件栏上显示该行所有栏目的详细内容。详情参考以下操作图例。

    ![](http://ww2.sinaimg.cn/large/0060lm7Tly1fjowptf8gog30ml0e4whq.gif)

8. 当所需数据内容全部添加到表格后，点击面板右上角的一个钢笔形状的图标（图标上方标注有Generate testStepCfg.ini）。此刻如果程序检测到之前check一列没有任何错误标记，则该表格生成的ini文件会覆盖并更新之前导入的ini文件；如果发现check一栏的错误尚有还未被更正的情况，程序会弹出提示框提示错误所在行，您可以选择忽视错误继续更新/生成ini文档。或者选择否，不生成文档，回头修改错误。建议，如果没有特殊情况，还请先修复错误后再选择生成文档，否则某些格式错误可能造成生成文档中某些部分的格式和您预想的不一致的情况。以下是错误提醒弹出框的视图：

    ![](https://i.loli.net/2017/09/22/59c47d2b83acc.png)

9. 当ini文件生成成功后，可以点击菜单栏上的exit按钮退出，或者点击菜单栏进行其他操作。注意，当\_testStepCfgEditor还没有运行结束时（生成ini文件后才算正常结束），是不可以在菜单栏创建新的\_testStepCfgEditor或者paraCfgEditor操作的，否则会弹出提示框，提示该VI进程仍然在运行中，必须结束该进程才可以进行其他操作（不限于帮助菜单，帮助菜单上的选项随时都可以按）。提示窗口如下图所示：

    ![](https://i.loli.net/2017/09/22/59c47eaf1dd06.png)

###_testStepCfgEditor的表格组成

_testStepCfgEditor的表格由6个栏目组成，分别是section，function，function arguments，function parameters，check以及comment。

下面对每个栏目的意义做分类解释：

1. section

    - section对应的即是ini文件中的section，在这个测试架构中，一个section对应的是一个testcase条目。
    
        ![](https://i.loli.net/2017/09/22/59c4870a941b4.png)

    - section一栏为空的行，归属于该列以上第一个section一栏不空的行所处的section，如下图所示：

        ![](https://i.loli.net/2017/09/22/59c484444ad75.png)

2. function

    function对应的即是函数，每一个函数实现一个特定的功能，基本上面板右侧的tree控件上已经包含了足够的测试用函数，而且这里函数的基本功能绝大多数都可以通过其名称得到一个大致的了解。用鼠标单击确认需要添加function的行，然后双击右侧面板tree控件上的function，即可自动填入function。当然你非要手写也没有问题，不过需要注意的是，这一栏唯一的限制是，这里可供填入的函数，必须存在于tree控件上。如果填入的函数不存在于tree控件上（比如你坚持手写但是不小心写错了），那么系统会报相应的错误。

    下图是双击tree控件添加函数的过程：

    ![](https://i.loli.net/2017/09/22/59c4b4065999f.gif)

    如果是你自己填，函数名填错了，那么check栏会提示你函数输入错误：

    ![](https://i.loli.net/2017/09/22/59c4b9f3b7176.gif)

3. function arguments

    function arguments即对应函数的实参，可以参考第三栏function parameters的形参样式来填入。如果填入的实参和形参的数据类型不符或者数目不符，check一栏会提示相应的错误。

    以下是一个实参与形参数目不符，报错的例子：

    ![](https://i.loli.net/2017/09/25/59c860bcc22c1.png)

    以下是一个实参与形参数据类型不符，报错的例子：

    ![](https://i.loli.net/2017/09/25/59c8623faa1ae.png)

4. function parameters

    function parameters即对应函数的形参，当你点击面板右侧tree控件添加函数的时候，该函数的形参会自动添加到该栏。填写函数实参的时候，可以参考该栏内容，填入正确类型的实参。需要注意的是，function parameters一栏的存在，仅仅是为了辅助用户填写实参。在最终生成的ini文档中，是没有形参的位置的。

5. comment

    comment即注释，适当的注释有利于用户回顾编写测试内容时的逻辑。这部分内容也会保留在最终生成的ini文件中，跟随在文本行末尾;//符号的后面。注：//的目的只是为了方便识别注释，真正区分注释和正文的关键在于；号。因此，即便用户在comment一栏中的起始没有填入符号//，脚本编辑器最终也会在生成的ini文件中，将符号//补上。

    以下是comment在应用和生成ini文件中的对应位置：

    ![](https://i.loli.net/2017/09/25/59c869f1eef70.png)

###_testStepCfgEditor的特殊格式说明

1. 首字符带\*的section

    section一栏的字符串中，如果首字符为\*，则说明该section所包含的测试序列可以作为一个变量被后续的首字符不含\*的正常section单独调用。

    举例说明，以下是一个首字符为\*的section：\*switchOffByLockSignal，这个case的功能是通过Lock signal来熄灭氛围灯。

    ![](https://i.loli.net/2017/09/22/59c4a7371adf5.png)

    鉴于灭灯是一个测试中经常需要用到的动作，如果每一次灭灯都需要重复\*switchOffByLockSignal中的这5个动作，显然非常不经济。但是如果将这5个动作放到一个首字符带\*的section中，那么将来灭灯只需要引用\*switchOffByLockSignal这个section的名称，即可实现对这5个动作的调用。

    调用格式： 在section中需要调用的行的function arguments一栏，填入：首字符为\*的section名称，后面加上=号即可完成调用。如下图所示：

    ![](https://i.loli.net/2017/09/22/59c4aecba370f.png)

    如果调用格式不对，check一栏会报相应的错误，并指示正确的填入方法。如下图所示，调用section的末尾漏掉了=号。

    ![](https://i.loli.net/2017/09/22/59c4afa5b06b4.png)

    需要注意的是：首字符带\*的section里，不应该再包含有其他的首字符带\*的section，以防止递归等情况下section的互相调用可能造成的死循环。如果在编辑器中出现这个问题，那么check一栏会自动报错。

2. 带\*号的实参

    某些情况下，某几个test case可能互相之间除了个别参数的数值是不同的，其余部分都是相同的，这种情况下，如果分别为这几个case撰写专门的用例肯定是不经济的。那么这时候，用户就可以采用带\*号的实参来处理这种情况，并且程序会自动默认这是一个符合函数形参数据类型的变量。

    其实带\*号的实参的本质目的是占位，延迟决定其指代数值。延迟到什么时候呢？延迟到生成.can文件后，待导入vTESTstudio，再由用户在vTESTstudio的parameter values面板中根据需求自行设定。那么具体是如何过渡到这个步骤的，我们会在后续部分详细说明。

    以下这个例子中，用例chkDrivingModeReqSigImpWhenIgnOff，调用了\*switchOnByDoorOpenSignalWithCheckWhenIgnOff和\*switchOffByLockSignal这两个case，如下图所示：

    ![](https://i.loli.net/2017/09/25/59c87377b7e5c.png)

    其中\*switchOnByDoorOpenSignalWithCheckWhenIgnOff这个被调用的case详情如下图所示：

    ![](https://i.loli.net/2017/09/25/59c8753adf895.png)

    \*switchOffByLockSignal这个被调用的case详情如下图所示：

    ![](https://i.loli.net/2017/09/25/59c8771dc157f.png)

    终上可以看出，用例chkDrivingModeReqSigImpWhenIgnOff中，一共有\*doorSignal,\*msWaitForTurnOn和\*drvModeReqVal这三个实参变量。
    
    那么，最终当用户使用vTESTstudio来调用这个case的时候，就可以通过vTESTstudio右侧自带的parameter Values面板，将相应的各实参可能的取值填入，然后由Combinatorics一栏来决定这三个参数间的数值匹配方式。

    ![](https://i.loli.net/2017/09/25/59c872cd2cd30.png)

3. 带|号的function

    某些情况下，从产品的某个状态，进入到产品的另一个状态，这个中间可以实现的方式可能不止一种。譬如需求文档中的状态机，就是一个很典型的例子。那么这个情况下，可以选择带|号的function来标注，这是实现状态的另一个路径。

    以下是一个采用了带|号的function的测试用例，其中带|号的function可以理解成上头第一个不带|号的function的另一个实现路径。

    ![](https://i.loli.net/2017/09/25/59c89ec4a73eb.png)

    其对应生成的ini文件如下图所示。譬如上图中第三行开始的signalSetting，|wait和|vtSysPwrSupVoltSet这几个函数，到了生成的ini文件中，就分别对应了step2中的3个不同的实现路径。

    ![](https://i.loli.net/2017/09/25/59c8a173e03d6.png)

    由于该用例调用了\*switchOnByDoorOpenSignalWithCheckWhenIgnOff这个case，程序会自动生成一个解析版的ini文件，将原ini中被调用的case展开，解析成其对应的测试函数步骤。

    \*switchOnByDoorOpenSignalWithCheckWhenIgnOff这个case对应的步骤如下图所示：

    ![](https://i.loli.net/2017/09/25/59c8753adf895.png)

    解析结果如下图所示：

    ![](https://i.loli.net/2017/09/25/59c8bc65651d0.png)

    程序除了生成相应的ini文件外，还会自动生成对应的.can文件，将这部分文件导入vTESTstudio才能最终在vTESTstudio中生成相应的测试序列。生成的.can文件的对应部分如下所示：

    ![](https://i.loli.net/2017/09/25/59c8b4902f615.png)

    首先说明，事实上，所有ini文件上的step其实对应了一个routeNum数组。默认情况下，该routeNum数组的所有元素均为0，即选择路径标识为0，即第一个路径。因为默认情况下是不存在带|号的function，所以仅有唯一的路径。但是，当带|号的function被引入之后，我们就必须对routeNum数组中的相应元素进行设置。这其中基本的对应关系是，step1对应了routeNum[0]，step2对应了routeNum[1]，以此类推……至于数组元素的取值，0代表第一条路径，1代表第二条路径，2代表第三条路径，以此类推。

    那么我们回过头来看解析版的ini，可以发现，带|号的function被引入进了从step7开始至step11终止的这5个step，因此需要特殊配置的routeNum数组中的相应元素就是[6]至[10]。

    由于此处的实际情形是只有3条路径，并且这3条路径分别对应了step7-11共同的第1路径，第2路径和第3路径，那么该程序可以被简化。

    手工将.can文件这部分修改如下：

    ![](https://i.loli.net/2017/09/25/59c8bee3289cf.png)

    最终当用户使用vTESTstudio来调用这个case的时候，就可以通过vTESTstudio右侧自带的parameter Values面板，将包括stepRouteNum在内的相应的各实参可能的取值填入，然后由Combinatorics一栏来决定这四个参数间的数值匹配方式。以下是针对上例的最终取值结果：

    ![](https://i.loli.net/2017/09/27/59cb074e04659.png)

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

    ![](https://i.loli.net/2017/09/26/59c9fbf857475.png)

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

        ![](https://i.loli.net/2017/09/27/59cafccc74809.png)

        最终通过vTESTstudio中的parameter values面板给同名字符串变量赋值，用例运行时，程序会自动采集同名字符串变量的赋值来运作相应的函数。

        ![](https://i.loli.net/2017/09/27/59cb062088327.png)

    - 针对section中含带\*号的实参，含带|号的function的情况

        这是最复杂的一种情况，在调用stateMachine函数时，除了指明section name，设定相应的paraPick数组，还需要设定routeNum数组。

        下面我们来看一个之前的例子，把之前这个案例再总结一下。

        ![](https://i.loli.net/2017/09/27/59cb0a90238a9.png)

        首先，解析版ini的step序号和routeNum元素编号的对应关系是，step1对应routeNum[0]，step2对应routeNum[1]，以此类推.

        其次，routeNum数组元素的取值和路径的对应关系，举图中step7这一行为例来说明。step7对应routeNum[6]，routeNum[6]取值为0，则取路径1，即step7选择操作函数为`signalSetting,RKEDoorLockCmd,1,1`；routeNum[6]取值为1，则取路径2，即step7选择操作函数为`wait,23000`；routeNum[6]取值为2，则取路径3，即step7选择操作函数为`vtSysPwrSupVoltSet,supint->out2,0`。

        再次，程序为了方便起见，给带|号的function的每一个step都分别设定了一个stepRouteNum变量，譬如routeNum[6]设定了一个stepRouteNum6的变量，routeNum[7]设定了一个stepRouteNum7的变量，以此类推。因为理论上，每一个routeNum都可以独立选取各自路径，但是事实上，不同的情况下可能会有不同的限制。譬如该例中，唯有当route[6]到route[10]这5个step的路径选取保持一致的时候，才符合需求文档的意义。那么这个时候，我们就可以将stepRouteNum6到stepRouteNum10这5个变量用同一个变量stepRouteNum来替换，这样变量的数量就可以大幅减少，这样parameter values面板的设定就会简易很多。

        不过这部分工作需要用户自己手动完成，因为程序不可能事先预知你对routeNum的限定条件。

        手工将.can文件这部分修改如下：

        ![](https://i.loli.net/2017/09/25/59c8bee3289cf.png)

        以下是针对上例的最终取值结果：

        ![](https://i.loli.net/2017/09/27/59cb074e04659.png)
        
###函数功能介绍

- 用户界面操作类函数

    1. testValidateTesterConfirmation
   
        函数原型： long TestValidateTesterConfirmation(char question[])

        功能： 弹出提示窗口，指示操作人员下一步的操作动作。

        参数：

        - question： 弹出窗口上显示的字符串内容。

        函数返回值： 

        ![](https://i.loli.net/2017/11/03/59fbc79f02e0e.png)

- 通讯协议类函数

    1. signalSetting
    
        函数原型： void signalSetting (char sigName[], float valueBase,int range) 

        功能： 给特定信号赋特定范围内的一个随机数。这个数的值为valueBase加上一个随机整数，0 ≤ 随机整数 < range。 

        参数：

        - sigName： 赋值信号在database上的名称。
        - valueBase： 赋值的基值
        - range： 赋值在基值上的随机整数范围偏差为0 — range-1

        函数返回值：无

    2. signalContSetting
   
        函数原型： void signalContSetting (char settingSignal[], float startVal, int range, long msGapTime)

        功能： 让特定信号从初始值startVal开始连续自增，增幅为1，一直自增到startVal+range-1为止。其中，每次赋值指令发出后，会在150ms后读取信号值，检测信号赋值是否成功，再等待msGapTime毫秒间隔，发送下一条赋值指令。

        参数：

        - sigName： 赋值信号在database上的名称。
        - startVal： 赋值的初值。
        - range： 赋值的增长范围。
        - msGapTime： 赋值的间隔时间（ms）。

        函数返回值： 无

    3. testEnableMsg
   
        函数原型： long TestEnableMsg (char aMessageName[])

        功能： 在使用TestDisableMsg函数屏蔽某周期性消息后，利用这条指令，可以重新激活该消息的发送。**注：该函数仅适用于由database定义的周期性消息。**

        参数：

        - aMessageName： 重新激活发送的周期性消息名称。

        函数返回值：

        - 0： No error。
        - -1: General error。

    4. testDisableMsg
   
        函数原型： long TestDisableMsg (char aMessageName[])

        功能： 屏蔽数据库中的某周期性消息的发送。**注：该函数仅适用于由database定义的周期性消息。**

        参数：

        - aMessageName： 屏蔽的周期性消息名称。

        函数返回值：

        - 0： No error。
        - -1: General error。

    5. linActivateSlot
   
        函数原型： long linActivateSlot(int tableIndex, int slotIndex)

        功能： 在使用linDeactivateSlot函数屏蔽某LIN消息后，利用这条指令，可以重新根据该消息在LDF文件中调度表的位置（tableIndex, slotIndex），来激活该消息的发送。

        参数：

        - tableIndex： 查看LDF文件，获取其在调度表中的tableIndex。该Index是从0开始的整数。
        - slotIndex： 查看LDF文件，获取其在调度表中的slotIndex。该Index是从0开始的整数。

        函数返回值：

        - 0： 激活发送失败。
        - 非0: 激活发送成功。

    6. linDeactivateSlot
   
        函数原型： long linDeactivateSlot(dword tableIndex, dword slotIndex)

        功能： 根据某LIN消息在LDF文件中调度表的位置（tableIndex, slotIndex），屏蔽该消息的发送。

        参数：

        - tableIndex： 查看LDF文件，获取其在调度表中的tableIndex。该Index是从0开始的整数。
        - slotIndex： 查看LDF文件，获取其在调度表中的slotIndex。该Index是从0开始的整数。

        函数返回值：

        - 0： 屏蔽失败。
        - 非0: 屏蔽成功。

    7. sendCanUdsDiagChkResp
   
        函数原型： long linDeactivateSlot(dword tableIndex, dword slotIndex)

        功能： 根据某LIN消息在LDF文件中调度表的位置（tableIndex, slotIndex），屏蔽该消息的发送。

        参数：

        - tableIndex： 查看LDF文件，获取其在调度表中的tableIndex。该Index是从0开始的整数。
        - slotIndex： 查看LDF文件，获取其在调度表中的slotIndex。该Index是从0开始的整数。

        函数返回值：

        - 0： 屏蔽失败。
        - 非0: 屏蔽成功。


    

    