###paraCfgEditor的使用说明

1. 确认工程中所有VI处于关闭状态，然后运行builder。注意，一定要保证工程中所有VI处于关闭状态，不然主VI运行会有异常，面板不能正常显示。

    ![](https://i.loli.net/2017/11/13/5a09371aa9134.png)

2. 点击弹出应用左上角的运行按钮，在菜单栏Editor选择paraCfgEditor。

    ![](https://i.loli.net/2017/11/13/5a08fd7093a2c.gif)

3. 在随后弹出的窗口中可以选择加载已有的paraCfg.ini文件进行后续的修改，或者可以在vTestStudioCfgEditor\cfg中新建空白的ini文件导入，从头制作一个新的paraCfg.ini文件.注意，必须导入一个存在的文档，无论是否空白。选择完毕，点击确认键。

    ![](https://i.loli.net/2017/09/27/59cb496c787ce.png)

4. 导入ini文件后，check一栏会显示相应的语法检测结果，如果出现某个key条目的数据类型不匹配或者数目不匹配或者符号格式等输入错误，check一栏会打上红色的×，并且会标注错误原因；检测正确的话，则会标注绿色的√。

    下图中同时包含有检测正确和错误的图示。需要注意的是，由于屏幕所限，每一列的宽度可能不足够展示该栏全部的信息，这个时候可以用鼠标双击你希望获得清楚信息的行，则该行每一栏的信息都会清晰地放大到上方的VIEW控件中。以下图为例，它展示的就是出错一行每一栏的详细信息。

    ![](https://i.loli.net/2017/11/13/5a08fecf95140.png)

5. 修正之前内容的时候，如果需要在两行之间插入新的一行，或者删除某一行内容，可以将鼠标置于表格部分相应的行上，按右键，会弹出一个菜单，根据具体需求，在菜单中选择“在前面插入行”或“删除行”。注意，不要对列进行操作，如果不慎操作错误，请在菜单栏中选择exit退出，再重新启动应用程序，导入paraCfgEditor。

    ![](https://i.loli.net/2017/11/13/5a09008b975c5.png)

6. 在原有的section下，添加一行新的key，只需在该行双击鼠标左键，key format一栏就会显示该section下相应的key所应遵循的格式，依次填写新的key name和key value即可。详情参考以下操作图例。

    ![](https://i.loli.net/2017/11/13/5a0901a2f0e1b.gif)

7. 如果需要在新的一行，添加新的section，可以在该行先点击鼠标左键，将鼠标置于该行任一栏内，然后点击面板右侧的tree控件里具体的某个具体的section名称，这时候该section的名称和具体的key fomat说明就会被添加到该行相应的栏内。详情参考以下操作图例。

    ![](https://i.loli.net/2017/11/13/5a090299ebd92.gif)

8. 在空白处填写新增key或section，当该行参数全部填写完毕后，如果需要审核该行参数的填写是否符合规范，只需将鼠标点击到除此行以外的其他任意行上，就能立刻看到该行check栏上的判定结果。如果需要查看该行的详细信息，只需鼠标左键双击该行，就可以在上部view控件栏上显示该行所有栏目的详细内容。详情参考以下操作图例。

    ![](https://i.loli.net/2017/11/13/5a0903e65b263.gif)

9. 当所需数据内容全部添加到表格后，点击面板右上角的一个钢笔形状的图标（图标上方标注有Generate ParaCfg.ini）。此刻如果程序检测到之前check一列没有任何错误标记，则该表格生成的ini文件会覆盖并更新之前导入的ini文件；如果发现check一栏的错误尚有还未被更正的情况，程序会弹出提示框提示错误所在行，用户可以选择忽视错误继续更新/生成ini文档。或者选择否，不生成文档，回头修改错误。建议，如果没有特殊情况，还请先修复错误后再选择生成文档，否则某些格式错误可能造成生成文档中某些部分的格式和您预想的不一致的情况。以下是错误提醒弹出框的视图：

    ![](https://i.loli.net/2017/11/13/5a09064d1dab5.png)

10. 当ini文件生成成功后，可以点击菜单栏上的exit按钮退出，或者点击菜单栏进行其他操作。注意，当paraCfgEditor还没有运行结束时（生成ini文件后才算正常结束），是不可以在菜单栏创建新的\_testStepCfgEditor或者paraCfgEditor操作的，否则会弹出提示框，提示该VI进程仍然在运行中，必须结束该进程才可以进行其他操作（不限于帮助菜单，帮助菜单上的选项随时都可以按）。提示窗口如下图所示：

    ![](https://i.loli.net/2017/11/13/5a0907095fb0e.png)

###paraCfgEditor的表格组成

paraCfgEditor的表格由6个栏目组成，分别是section，key name，key value，key format，check以及comment。

下面对每个栏目的意义做分类解释：

1. section

    - section对应的即是ini文件中的section，在这个文本中，section对应的是配置项的分类。
    
        譬如下图中，vt2516Cfg这个section，这部分的内容就和vt2516这块板卡的配置有关。
    
        ![](https://i.loli.net/2017/11/13/5a0907f82d00d.png)

    - section一栏为空的行，归属于该列以上第一个section一栏不空的行所处的section，如下图所示：

        ![](https://i.loli.net/2017/11/13/5a0908f95c904.png)

    - section一栏可供选择的名称，通通列于面板右侧的tree控件上。用鼠标单击确认需要添加新的section的行，然后双击右侧面板tree控件上的section，即可自动将该section的名称填入section一栏。当然你非要手写section也没有问题，不过需要注意的是，这里可供填入的section，必须存在于tree控件上。如果填入的section不存在于tree控件上（比如你坚持手写但是不小心写错了），那么系统会报相应的错误。

        下图是填入section不存在于tree控件中所报错误的图示：
        
        ![](https://i.loli.net/2017/11/13/5a0909c53a219.png)
      

2. key name

    key name对应的即是ini文件中各section下各个key的名字。key name应尽量根据key format中相应部分的格式，取有意义，有识别度的名称。

    譬如下图中，vt2516Cfg这个section，根据key format的定义，key name应该代表该PIN的名称。

    ![](https://i.loli.net/2017/11/13/5a090b4a7d7bb.png)

3. key value

    key value对应的即是ini文件中各section下各个key相应的值。这部分必须根据key format一栏中对应value的格式来填入。如果填入的key value和key format中定义的数据类型或者数目不符，check一栏会提示相应的错误。

    以下是一个key value与key format定义中数目不符，报错的例子：

    ![](https://i.loli.net/2017/11/13/5a090c0bb9cd8.png)

    以下是一个key value与key format数据类型不符，报错的例子：

    ![](https://i.loli.net/2017/11/13/5a090cac8ea05.png)

4. key format

    key format对应的即是key的格式，包括key name和key value的格式。当用户点击面板右侧tree控件添加section的时候，该section对应的key format会自动添加到该栏。填写key相应的参数时，可以参考该栏内容，填入正确类型的参数。需要指出的是，key format一栏的存在，仅仅是为了辅助用户填写key。在最终生成的ini文档中，是没有key format的位置的。

    除此之外，key format还有一种特殊的格式需要注意。key format中，如果key value部分的定义里，参数中带有\_i，说明这是一个通项的定义公式，这部分参数的实际配置可以是整数个组别的带\_i参数类型。

    举例说明，下图中，key format里头就包含了5个带\_i的参数，而实际的key value则包含10组的这5个带\_i的参数.

    ![](https://ooo.0o0.ooo/2017/11/13/5a090d6d6599d.png)
    
5. comment

    comment即注释，适当的注释有利于用户回顾编写key时的逻辑，这部分内容也会保留在最终生成的ini文件中，跟随在文本行末尾的;//符号的后面。注：//的目的只是为了方便识别注释，真正区分注释和正文的关键在于;号。因此，即便用户在comment一栏中的起始没有填入符号//，脚本编辑器最终也会在生成的ini文件中，将符号//补上。

    以下是comment在应用和生成ini文件中的对应位置：

    ![](https://i.loli.net/2017/11/13/5a090f4bf1efb.png)

###paraCfgEditor的生成文档说明

paraCfgEditor应用程序在正常运行结束后，会生成唯一的文档paraCfg.ini。

该文档是运行paraCfgEditor程序时，首先要求导入的文档。paraCfg.ini是推荐输入的文件名，当然你也可以选择其他的文件名。

![](https://i.loli.net/2017/09/27/59cb496c787ce.png)

导入后，你可以进行相应的修改，新增或者删除等操作。

当所需数据内容全部添加完成后，点击面板右上角的一个钢笔形状的图标（图标上方标注有Generate paraCfg.ini）实现最终文件生成，这时候会根据之前在应用程序表格中的相应内容，自动更新覆盖之前导入的文本（文件名保持不变）。

###各section的key format详细说明

- vtSystem板卡相关的基础配置

    1. vt2516Cfg

	    该section是关于产品pin相对于vt2516板卡的连接配置。

	    vt2516是一个功能强大的模块，可以提供AI,AO,DI,DO,PWM INPUT,PWM OUTPUT等各种功能，基本涵盖产品中除了PWR,GND,CAN,LIN端子外的所有pin的测试需求。

        key format的格式为：`pinname = int moduleNo,int channelNo`，意即产品上的某个pin在线束另一端对应于哪个模块号的vt2516板卡上的哪个通道。

        **注：这里key name的值是产品的PIN名称，这个key name值后续也会被其他section引用。所以务必保证前后所有section处pinname名称的统一。**

	    应用举例：
	    <pre>
	    [vt2516Cfg]
	    IGN = 9,6
	    ACC = 9,5
	    Detent = 9,2
	    PWM_IN = 9,3
	    PWM_OUT = 9,1
	    </pre>

	    该section中的内容会影响后续产品的PWM输出波形检测，vt2516通道的固定电压的DO设置，vt2516通道的AO设置，vt2516通道的PWM输出波形设置，vt2516通道的负载连接状态等。

	    库函数中的prodPwmOutChk,chFixVoltDOSet,chAOSet,chPwmOutSet,chLoadConnectStatSet等函数均会直接调用该section的内容，而btnPrsImpOnSpecPwmChk,chRamVoltDOSet,sigDirMulStatInSet等函数则会间接调用该section内容。

    2. vLevelCfg

	    该section是关于vt2516板卡的数字输出电平的配置，电平的大小在设置数值范围内随机变动，并且值为整数。如果pin采用的电平输入，均为接电源或者接地的固定高低电平，就不需要设置该项。

        key format的格式为：`pinname = int vInactiveLevelBase,int vInactiveLevelRange,int vActiveLevelBase,int vActiveLevelRange`，意即针对于产品上的某个pin，vt2516会给予的inactive电平的基值和范围以及active电平的基值和范围。

        **注：这里key name的值是产品的PIN名称，这个key name值也会被其他section引用。所以务必保证前后所有section处pinname名称的统一。**

	    应用举例：
	    <pre>
	    IGN = 0,4,8,5
	    ACC = 0,4,8,5
	    Detent = 8,5,0,4
	    </pre>

	    以上第1行为例说明：`IGN = 0,4,8,5`，意即某vt2516的通道输出为pin IGN提供0V<=低电平<4V，8V<=高电平<8+5=13V的数字电平输入，且该pin为高有效。

	    同理，以上例中的第3行为例：`Detent = 8,5,0,4`,意即某vt2516的通道输出为pin Detent提供8V<=高电平<8+5=13V，0V<=低电平<4V的数字电平输入，且该pin为低有效。

	    该section中的内容设置会影响后续的产品各DI pin的数字输入电压配置。

	    库函数中的chRamVoltDOSet函数会直接调用该section的内容，而函数sigDirTwoStatInSet则会间接调用该section内容。

    3. vt7001Cfg

	    该section是关于vt7001板卡的电源输出方式的配置。

        key format的格式为：`pwrConnectWay =int moduleNo,enum vt7001InterConnectionMode interConnectionMode,enum vt7001OutputChannelNo outChNum`，意即定义了一种vt7001板卡供电的内部连接方式，指明了这种方式下，使用了哪个模块号的板卡，内部的连接模式，以及电源的输出通道。

        其中enum vt7001InterConnectionMode的取值范围为:

        <pre>
          supint = 0, 
          sup1 = 1, 
          sup2 = 2, 
          supint_sup1 = 3, 
          supint_sup2 = 4, 
          sup1_supint = 5, 
          sup1_sup2 = 6, 
          sup2_supint = 7, 
          sup2_sup1 = 8, 
          sup_series = 9, 
          sup_parallel = 10
        </pre>

        enum vt7001OutputChannelNo的取值范围为：

        <pre>
          out1 = 1,
          out2 = 2
        </pre>

        对于以上这两个参数的理解，可以参考下图。如果还有不清楚的地方，请参考vector公司的vtSystem帮助文档手册。

        ![](https://i.loli.net/2017/11/13/5a0937e332377.png)

	    应用举例：
	    <pre>
	    supint->out2 = 12,0,2
	    </pre>

	    上例中的`supint->out2 = 12,0,2`，意即，定义了一种名为supint->out2的供电方式，这种方式下，使用了所属模块号为12的vt7001板卡，板卡内选取internal power supply，输出通道为OUT2。

	    该section中的内容设置会影响后续vt7001板卡的电源的连接方式，电源电压的设置，以及板卡电源端电压、电流的读取。

	    库函数中vtSysPwrSupInit，vtSysWithExPwrSupInit，vtSysPwrSupVoltSet，vtSysExPwrSupSet，vtSysPwrSupVoltGet，vtSysPwrSupCurrGet等函数会直接调用该section的内容。

    4. pwmWaveCfg

	    该section是关于vt2516板卡的PWM输出波形的配置，目的是为产品的PWM-INPUT pin端提供特定的PWM输入以令产品进入某特定状态。

        key format的格式为：`prodStat = int freq,int voltLow,int voltHigh,int dutyBase,int dutyRange`，意即定义了产品进入状态prodStat，所需的pin端PWM输入频率，低高电平伏值，以及占空比基值和范围。

        **注:这个key的目的主要是配置台架给到产品某一pin端具体的PWM输入波形，使产品进入某种特定状态，其中的key name表示产品具体的某一状态，该值会被后续的section：sigDirMulStatInCfg引用。因此，该section的key name务必和section:sigDirMulStatInCfg中的key name保持一致。**

	    应用举例：
	    <pre>
	    P = 100,0,12,8,5
	    R = 100,0,12,18,5
	    N = 100,0,12,28,5
	    D = 100,0,12,38,5
	    No = 100,0,12,48,5
	    ANY = 100,0,12,0,100
	    </pre>

	    以上第1行为例：`P = 100,0,12,8,5`,意即为了让产品进入P状态，vt2516板卡应为产品相应的pin端提供100Hz，低电平为0V，高电平为12V，8%<=占空比<8+5=13%的PWM波形输入。

	    该section中的内容设置会影响后续vt2516板卡的PWM输出波形的设置。库函数中的函数chPwmOutSet会直接调用该section的内容，函数sigDirMulStatInSet会间接调用该section内容。

    5. pwmTimeCfg

        该section是针对产品在某个模式下由某pin端产生的PWM波形从发生变化伊始，到稳定，到下降或消失，这三个阶段的匹配参数定义。这里的上升过程，是指占空比增大的过程；下降过程，是指占空比减小的过程。

        key format的格式为：`productPwmOutMode = char pinName[],float freqAfterRise,float dutyAfterRise,float freqAfterFall,float dutyAfterFall,int dutyDeviation,int maxRiseTime,int msKeepTime,int msKeepTimeDeviation,int maxFallTime`，意即定义了产品所处的PWM输出的某个特定模式下，具体是由哪个pin生成了PWM，波形上升稳定后的频率、占空比，波形下降后达到的（未必是稳定值，可以是中间量）频率、占空比，整个过程中占空比允许的偏差，波形占空比上升到指定值允许的最大时间(ms)，波形占空比维持稳定的时间(ms)及偏差(ms)，波形占空比下降到指定值允许的最大时间(ms)。

        应用举例：
        <pre>
        Mode2_G_Dc0-full-0 = Zone1_G+,200,20,0,0,2,1000,20000,100,2000
        Mode2_B_Dc0-full-0 = Zone1_B+,200,96,0,0,2,1000,20000,100,2000
        Mode2_G_Dc0-full-half = Zone1_G+,200,20,200,10,2,1000,20000,100,1000
        Mode2_B_Dc0-full-half = Zone1_B+,200,96,200,48,2,1000,20000,100,1000
        </pre>

        以上第1行为例：`Mode2_G_Dc0-100-0 = Zone1_G+,200,20,0,0,2,1000,20000,100,2000`，这里定义的productPwmOutMode名称为Mode2\_G\_Dc0-full-0，字面意思即Mode2\_G模式下PWM占空比从0上升到最大值再跌回0这么一个过程，这个过程对应了产品的pin是Zone1_G+，占空比上升结束时，频率应为200Hz，占空比应为20%，占空比下降，达到频率0Hz，占空比0，整个过程中占空比的偏差为±2%，波形占空比上升到20%允许的最大时间为1000ms,波形占空比维持在20%的时间为20000ms，偏差为±100ms，波形占空比下降到0允许的最大时间为2000ms。

        以上第3行为例：`Mode2_G_Dc0-full-half = Zone1_G+,200,20,200,10,2,1000,20000,100,1000`，这里定义的productPwmOutMode名称为Mode2\_G\_Dc0-full-half，字面意思即Mode2\_G模式下PWM占空比从0上升到最大值再跌回一半这么一个过程，这个过程对应了产品的pin是Zone1_G+，占空比上升结束时，频率应为200Hz，占空比应为20%，占空比下降，频率达到200Hz，占空比达到10%，整个过程中占空比的偏差为±2%，波形占空比上升到20%允许的最大时间为1000ms,波形占空比维持在20%的时间为20000ms，偏差为±100ms，波形占空比下降到10%允许的最大时间为1000ms。

        该section中的内容设置会影响后续对PWM输出过程的时间测量。库函数中的prodPwmOutRisingEdgeMeas,prodPwmOutKeepTimeMeas,prodPwmOutFallingEdgeMeas等函数会直接调用该section的内容。

- 产品操作及状态设置相关的配置

    1. prodOperWithPinStatImpOnSpecSigCfg

	    该section是针对产品上的特定按钮或pin脚等操作对特定信号产生的影响的配置。

        key format的格式为：`operationMode = char DirPinName[],char signame_i[],float updateSigVal_i,int msWaitBefCheck_i,int demandRes_k_i,int demandRes_b_i`,意即对产品进行某种方式的操作，该操作产生的结果会受DirPinName[]这个pin的状态影响，最终的影响会作用于信号signame\_i[]，该信号可能会被更新成updateSigVal\_i，检测前需要等待的时间(ms)，判定该信号是否应该被更新成值updateSigVal\_i，是由DirPinName[]这个pin的active或inactive的状态，以及参数demandRes\_k\_i,demandRes\_b\_i共同决定的。计算公式为：demRes = demandRes\_k\_i*(DirPinName[]的active或inactive状态，其中active=1，inactive=0，由section:vLevelCfg的key值区间判定) +demandRes\_b\_i。如果demRes = 1，则要求信号signame\_i[]的值更新为updateSigVal\_i；如果demRes = 0，则要求信号signame\_i[]的值不可更新为updateSigVal\_i。

	    应用举例：
	    <pre>
	    P = IGN,CF_Lvr_PButtonStatus,1,500,0,1,CF_Lvr_PButtonStatus_Reversed,2,500,0,1
        R = IGN,CF_Lvr_RButtonStatus,1,500,1,0,CF_Lvr_RButtonStatus_Reversed,2,500,1,0
	    </pre>

	    以上例中的第1行为例：`P = IGN,CF_Lvr_PButtonStatus,1,500,0,1,CF_Lvr_PButtonStatus_Reversed,2,500,0,1`,意即产品操作方式为P按键的按压，这个按压的操作结合IGN的电平状态，会对CF\_Lvr\_PButtonStatus和CF\_Lvr\_PButtonStatus\_Reversed这两个信号产生影响。其中对CF\_Lvr\_PButtonStatus产生的影响是，P按钮按压500ms后，CF\_Lvr\_PButtonStatus有可能会被更新为1，更新与否取决于内部参数demRes。当demRes = 1时，则表示程序认定该按钮的按压应该会导致该信号更新为1；当demRes = 0时，则表示程序认定该按钮的按压不会导致该信号更新为1。内部参数demRes取值的计算公式是：demRes = demandRes\_k × [IGN的状态(Active=1，Inactive=0)]+demandRes\_b。这里，demandRes\_k1=0,demandRes\_b1=1，因此demRes = 1，也就是说，无论IGN处在何种状态，P按钮的按压都应该会让信号CF\_Lvr\_PButtonStatus在500ms内更新为1.同理，无论IGN处在何种状态，P按钮的按压都应该会让信号CF\_Lvr\_PButtonStatus\_Reversed在500ms内更新为2.

	    该section中的内容设置会影响后续产品操作（比如对按钮的按压，或对某个PIN的高低电平输入变化）对相应信号变化的判断。库函数中的函数prodOperWithPinStatImpOnSpecSigChk会直接调用该section的内容。

    2. prodOperWithPinStatImpOnSpecPwmCfg

	    该section是针对产品上的特定按钮或pin脚等操作对产品PWM输出波形影响的配置。

        key format的格式为：`operationMode = char DirPinName[],char outPwmPinName_i[],int freqk_i,int freqb_i,int dutyk_i,int dutyb_i,int deviation_i`，意即对产品进行某种方式的操作，该操作产生的结果会受DirPinName[]这个pin的状态影响，最终的影响会作用于outPwmPinName\_i[]这个pin的PWM输出波形上。其中，输出波形的频率由DirPinName[]这个pin的active或inactive的状态，以及参数freqk\_i,freqb\_i共同决定，计算公式为：freq = freqk\_i × (DirPinName[]的active或inactive状态，其中active=1，inactive=0，由section:vLevelCfg的key值区间判定)+freqb\_i；输出波形的占空比由DirPinName[]这个pin的active或inactive的状态，以及参数dutyk\_i,dutyb\_i共同决定，计算公式为：duty = dutyk\_i*(DirPinName[]的active或inactive状态，其中active=1，inactive=0，由section:vLevelCfg的key值区间判定)+dutyb\_i,在测量过程中，占空比允许的偏差为±deviation\_i% 。

	    应用举例：
	    <pre>
	    IDLE = IGN,PWM_OUT,0,100,0,50,3
	    P = IGN,PWM_OUT,0,100,0,10,3
	    R = IGN,PWM_OUT,0,100,-30,50,3
	    N = IGN,PWM_OUT,0,100,-20,50,3
	    D = IGN,PWM_OUT,0,100,-10,50,3
	    PRelease = IGN,PWM_OUT,0,100,-20,70,3
	    </pre>

	    以上例中的第3行为例：`R = IGN,PWM_OUT,0,100,-30,50,3`。意即产品操作方式为R按键的按压，这个按压的操作结合IGN的电平状态，会对产品的PWM\_OUT pin上产生的PWM波造成影响。其中，生成PWM波形的频率依据计算公式：freq = freqk\_i × [IGN的状态(Active=1，Inactive=0)]+freqb\_i，代入freqk1=0,freqb1=100，因此，freq=100Hz，也就是说，无论IGN处在何种状态，输出频率的大小都会是100Hz；生成PWM波形的占空比依据计算公式：duty = dutyk\_i × [IGN的状态(Active=1，Inactive=0)]+dutyb\_i，代入dutyk1=-30，dutyb1=50，因此当IGN处在Active状态下，duty=20%；当IGN处在Inactive状态下，duty=50%。整个测量过程中，允许占空比测量结果的偏差为±3% 。

	    该section中的内容设置会影响后续产品操作（比如按压产品按钮，或对某个PIN的高低电平输入变化），测试台架对产品相应PIN输出PWM波形的判断。库函数中的函数prodOperWithPinStatImpOnSpecPwmChk会直接调用该section的内容。

    3. prodOperWithSigStatImpOnSpecPwmCfg

	    该section是针对产品上的特定按钮或pin脚等操作对产品PWM输出波形影响的配置。

        key format的格式为：`operationMode = char DirSigName[],char outPwmPinName_i[],int freqk_i,int freqb_i,int dutyk_i,int dutyb_i,int deviation_i`，意即对产品进行某种方式的操作，该操作产生的结果会受DirSigName[]这个信号的状态影响，最终的影响会作用于outPwmPinName\_i[]这个pin的PWM输出波形上。其中，输出波形的频率由DirSigName[]这个信号的active或inactive的状态，以及参数freqk\_i,freqb\_i共同决定，计算公式为：freq = freqk\_i × (DirSigName[]的active或inactive状态，其中active=1，inactive=0)+freqb\_i；输出波形的占空比由DirSigName[]这个信号的active或inactive的状态，以及参数dutyk\_i,dutyb\_i共同决定，计算公式为：duty = dutyk\_i*(DirSigName[]的active或inactive状态，其中active=1，inactive=0)+dutyb\_i,在测量过程中，占空比允许的偏差为±deviation\_i% 。

	    应用举例：
	    <pre>
        Mode0 = PosLmpSts,Zone1_R+,0,0,0,0,2,Zone1_G+,0,0,0,0,2,Zone1_B+,0,0,0,0,2
        color_change_sw->Mode1_4 = PosLmpSts,Zone1_R+,200,0,-25,100,2,Zone1_G+,0,0,0,0,2,Zone1_B+,0,200,-1,3,2
        color_change_sw->Mode2_5 = PosLmpSts,Zone1_R+,0,0,0,0,2,Zone1_G+,0,200,-5,20,2,Zone1_B+,0,200,-24,96,2
        color_change_sw->Mode3_6 = PosLmpSts,Zone1_R+,200,0,-25,100,2,Zone1_G+,0,200,-8,32,2,Zone1_B+,0,0,0,0,2
	    </pre>

	    以上例中的第2行为例：`color_change_sw->Mode1_4 = PosLmpSts,Zone1_R+,200,0,-25,100,2,Zone1_G+,0,0,0,0,2,Zone1_B+,0,200,-1,3,2`。意即产品的操作方式为color\_change\_sw的按压，这个按压的操作结合信号PosLmpSts的状态，会对产品的Zone1\_R+，Zone1\_G+及Zone1\_B+ 这三个pin上产生的PWM波形造成影响。其中，Zone1\_R+生成的PWM波形频率依据计算公式：freq = freqk\_i × [PosLmpSts的值(Active=1，Inactive=0)]+freqb\_i，代入freqk1=200,freqb1=0，因此，Zone1\_R+的PWM波形频率，当PosLmpSts=0时，freq1=0Hz，当PosLmpSts=1时，freq1=200Hz；生成PWM波形的占空比依据计算公式：duty = dutyk\_i × [PosLmpSts的值(Active=1，Inactive=0)]+dutyb\_i，代入dutyk1=-25，dutyb1=100，因此，Zone1\_R+的PWM波形占空比，当PosLmpSts=0时，duty1=100%，当PosLmpSts=1时，duty1=75%，允许的偏差范围为±2%。同理，Zone1\_G的PWM波形频率，freq2恒等于0Hz；duty2恒等于0，允许的偏差范围为±2%。Zone1_B+的PWM波形频率，freq3恒等于200Hz；PWM波形占空比，当PosLmpSts=0时，duty3=3%，当PosLmpSts=1时，duty3=2%，允许的偏差范围为±2%；

	    该section中的内容设置会影响后续产品特定信号变化导致的测试台架对产品相应PIN输出PWM波形的判断。库函数中的函数prodOperWithSigStatImpOnSpecPwmChk会直接调用该section的内容。

    4. sigDirTwoStatInCfg

	    该section是针对设定产品进入某二态之一的状态（该状态由某signal值主导，如果该signal失效，则由产品相应PIN的高低电平状态决定），所需提供的输入配置。

        key format的格式为：`pinName = char msgName[],char sigName[],float sigInactVal,float sigActVal`，意即，产品的该状态设定，和key等号左侧这个pin的电平高低状态有关，也和key等号右侧的message上的某个signal的inactive和active值相关，并且信号的影响占主导作用，只有当信号中断的情况下，系统才参考pin的电平高低状态。

        **注意，该section的key name中的pinName和section vLevelCfg中的pinName必须一致，因为会调用section vLevelCfg中的电平范围定义。**

	    应用举例：
	    <pre>
	    Detent = EV_CP2,CF_GWAY_Detentout,0,1
	    </pre>

	    上例中的`Detent = EV_CP2,CF_GWAY_Detentout,0,1`，意即，Detent的状态由PIN Detent以及message EV_CP2中的信号CF\_GWAY\_Detentout的值共同决定，其中0为该信号的inactive值，1为该信号的active值。至于Detent这个pin端的电平影响，则参加vLevelCfg这个section对inactive及active状态的电平设定。

	    该section中的内容会影响后续产品状态的设置。库函数中的sigDirTwoStatInSet函数会直接调用该section的内容。

    5. sigDirMulStatInCfg

	    该section是针对为使产品进入某多态之一的状态（该状态由某signal值主导，如果该signal失效，则由产品相应的PWM_INPUT pin的PWM状态决定），所需提供的输入配置。

        key format的格式为:`prodStat = char msgName[],char sigName[],int sigValBase,int sigValRange,char pinName[]`，意即，为了让产品进入key等号左侧的状态，需要设置msgName[]这个消息上的信号sigName[]，信号的随机取值范围为sigValBase<=sigVal<sigValBase+sigValRange,如若该信号失效，则需设置pinName[]这个引脚上相应的PWM输入波形，具体的波形设置，需参看section：pwmWaveCfg。

        **注意，该section的key name:prodStat和section pwmWaveCfg中的prodStat必须一致。**

	    应用举例：
	    <pre>
	    P = VCU1,CF_Vcu_GarSelDisp,0,1,PWM_IN
	    R = VCU1,CF_Vcu_GarSelDisp,7,1,PWM_IN
	    N = VCU1,CF_Vcu_GarSelDisp,6,1,PWM_IN
	    D = VCU1,CF_Vcu_GarSelDisp,5,1,PWM_IN
	    No = VCU1,CF_Vcu_GarSelDisp,1,4,PWM_IN
	    </pre>

	    以上例中的第1行为例：`P = VCU1,CF_Vcu_GarSelDisp,0,1,PWM_IN`，意即，产品进入状态P由message VCU1中的信号CF\_Vcu\_GarSelDisp的值（其中CF\_Vcu\_GarSelDisp的值设为0<=CF_Vcu_GarSelDisp<0+1之间的随机整数，即CF\_Vcu\_GarSelDisp=0）以及PIN PWM_IN的波形共同决定，但是信号的值起决定性的作用。

	    该section中的内容设置会影响后续产品状态的设置。库函数中的函数sigDirMulStatInSet会直接调用该section的内容。

    6. specStatImpOnSigCfg

	    该section是针对产品是否进入某种状态的验证配置。当然，你也可以理解为是进入某种状态后相应地对某信号产生的影响的配置。

        key format的格式为：`prodStat = char sigName[],float demandVal,int msWaitBefCheck`，意即，产品进入key等号左侧的特定状态后，信号sigName[]应在msWaitBefCheck后更新为值demandVal。

        **注意，此处的key主要是配置状态对信号的影响，一般是跟随之前sigDirMulStatInCfg处section进行的状态设置后，作为对是否进入该状态的验证。因此，该section的keyname：prodStat应该和sigDirMulStatInCfg中的prodStat保持一致。**

	    应用举例：
	    <pre>
	    P = CF_Lvr_IndicatorStatus,1,1000
	    R = CF_Lvr_IndicatorStatus,2,1000
	    N = CF_Lvr_IndicatorStatus,3,1000
	    D = CF_Lvr_IndicatorStatus,4,1000
	    No = CF_Lvr_IndicatorStatus,0,1000
	    </pre>

	    以上例中的第1行为例：`P = CF_Lvr_IndicatorStatus,1,1000`，意即，进入状态P后，信号CF\_Lvr\_IndicatorStatus的值将在1000ms之内更新为1.

	    该section中的内容设置会影响后续产品对是否进入某特定状态的验证。库函数中的函数specStatImpOnSigChk会直接调用该section的内容。

- 通讯相关的配置

    1. UDS Services

	    该section是针对产品的各种UDS诊断服务指令的配置。

        key format的格式是：`UDS Service Name = int sendMsgId,int sendMsgDataLen,qword sendMsgData,int recMsgId,int offsetByteChkPos,int chkByteLen,qword chkRecMsgPartData`，意即，某条UDS诊断服务的通讯方式是，上位机发送诊断指令，其中ID为sendMsgId，字节长度为sendMsgDataLen，发送的字节内容为sendMsgData，产品接收到上位机指令后，返回正确指令，其中ID应为recMsgId，并确保，从offsetByteChkPos字节起的共chkByteLen个字节长度，字节内容应为chkRecMsgPartData。

	    应用举例：
	    <pre>
        Read DTC = 0x7b6,8,0x031902ff00000000,0x7be,2,3,0x5902ff
	    </pre>

	    以上为例：`Read DTC = 0x7b6,8,0x031902ff00000000,0x7be,2,3,0x5902ff`，意即，要使用UDS的DTC读取服务，需要发送的消息为，ID=0x7b6，数据长度=8，发送的字节内容为0x031902ff00000000。产品接收诊断指令后的正确反馈为，ID=0x7be,且该反馈从第2个byte开始的3个byte长度的字节内容，如果符合0x5902ff，那么测试系统会判断它是正确的UDS反馈。

	    该section中的内容设置会影响后续产品在kostia下的诊断指令收发验证。库函数中的sendCanUdsDiagChkResp，sendLinUdsDiagChkResp等函数会直接调用该section的内容。

    2. Kostia Services

	    该section是针对产品的各种kostia诊断服务指令的配置。

        key format的格式是：`Kostia Service Name = int sendMsgId,int sendMsgDataLen,qword sendMsgData,int recMsgId,int offsetByteChkPos,int chkByteLen,qword chkRecMsgPartData`，意即，某条Kostia诊断服务的通讯方式是，上位机发送诊断指令，其中ID为sendMsgId，字节长度为sendMsgDataLen，发送的字节内容为sendMsgData，产品接收到上位机指令后，返回正确指令，其中ID应为recMsgId，并确保，从offsetByteChkPos字节起的共chkByteLen个字节长度，字节内容应为chkRecMsgPartData。

	    应用举例：
	    <pre>
	    Login-Request = 0x62c,8,0x014b4f5354414c5f,0x62d,0,8,0x014b4f5354414c5f
	    Read VM_SW_Internal = 0x62c,8,0x040012060C000000,0x62d,0,1,0x04
	    Read VM_SW_External = 0x62c,8,0x04000C060C000000,0x62d,0,1,0x04
	    </pre>

	    以上例中的第1行为例：`Login-Request = 0x62c,8,0x014b4f5354414c5f,0x62d,0,8,0x014b4f5354414c5f`，意即，要进入kostia的Login-Request服务，需要发送的消息为，ID=0x62c，数据长度=8，发送的字节内容为0x014b4f5354414c5f。产品接收诊断指令后的正确反馈为，ID=0x62d,且该反馈从第0个byte开始的8个byte长度的字节内容，如果符合0x014b4f5354414c5f，那么测试系统会判断它是正确的Kostia反馈。

	    该section中的内容设置会影响后续产品在kostia下的诊断指令收发验证。库函数中的sendCanKostiaDiagChkResp，sendLinKostiaDiagChkResp等函数会直接调用该section的内容。