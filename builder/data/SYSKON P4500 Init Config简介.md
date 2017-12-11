###SYSKON P4500 Init Config简介

SYSKON P4500 Init Config是用来初始化SYSKON P4500外接电源的基础配置的。如果用户在使用vt7001板卡的时候，希望选择SYSKON P4500作为外接电源接入，那么在使用vtSysWithExPwrSupInit，vtSysExPwrSupSet等相关函数前，必须先初始化SYSKON P4500的基础配置。

具体的操作面板如下图所示：

![](https://s1.ax1x.com/2017/12/10/HVfTe.png)

以下对操作面板上的几个控件做详细说明：

1. Instr. Descriptor：该控件是用来选择SYSKON P4500和上位机之间的接口的；

2. Baud Rate：该控件是用来设定上位机和SYSKON P4500之间USB通讯的传输速率的。一般该速率的取值应为19200；

3. OCP Level：该控件是用来设定SYSKON P4500的Over Current Protection值的。设定生效后，该电源电流输出的最大值就不会超过该设定值；

4. OVP Level：该控件是用来设定SYSKON P4500的Over Voltage Protection值的。设定生效后，该电源电压输出的最大值就不会超过该设定值；

5. Output State：该控件是用来设定该面板上各控件的设定值是否生效，SYSKON P4500上是否向外输出电压的。当该控件的值为ON时，则确认之前面板上各控件的设定生效，该电源即刻对外输出电压。当该控件的值为OFF时，则该面板各控件上的值暂未生效，用户仍可以继续对各控件配置值做相应的修改，此时该电源并不向外输出电压；

6. Output Voltage：该控件是用来显示，当Output State为ON时，SYSKON P4500对外输出的电压值的。当Output State为OFF时，SYSKON P4500并不对外输出电压，因而此时该栏空白，没有数值显示；

7. Output Current：该控件是用来显示，当Output State为ON时，SYSKON P4500对外输出的电流值的。当Output State为OFF时，SYSKON P4500并不对外输出电压，因而此时该栏空白，没有数值显示。

