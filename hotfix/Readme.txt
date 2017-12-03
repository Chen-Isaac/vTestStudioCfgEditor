正常修改VI源代码的步骤：

1. 解压缩Write Key (String without quotation) workaround.7z，将Write Key (String without quotation) workaround.vi置于C:\Program Files (x86)\National Instruments\LabVIEW 2010\vi.lib\Utility\config.llb下；
2. 解压缩gmpsp.7z，将gmpsp文件夹置于C:\Program Files (x86)\National Instruments\LabVIEW 2010\instr.lib下；

保证EXE正常运行的步骤：

1. \instr.lib\gmpsp置于vTestStudioCfgEditor\builder下，保证SYSKON P4500 Init Config.vi在EXE running状态下可以正常运行。