# Tanner 软件的使用教程——以反相器电路为例
## 一、 使用 S-Edit 绘制原理图
### 原理图绘制部分
1. 打开 S-Edit 单击 *New Design* 新建一个项目![[Pasted image 20231114171725.png]]
2. 自定义项目名称和存储地点![[Pasted image 20231114171808.png]]
3. 添加存储库![[Pasted image 20231114171934.png]]
其中存储库的链接在打包下载的文件中，在路径`~\2023-2024-1EDA参考资料和软件\tanner\Libraries\Libraries\All` 下寻找文件 All.tanner 添加库
4. 确认全部库添加到项目中，点击 *Cell > New View* 新建原理图绘制![[Pasted image 20231114172307.png]]![[Pasted image 20231114172549.png]]
***PS1*** S-Edit 软件的放大为**直接滚动鼠标滚轮**，向上/下翻页为 **Ctrl + 滚动鼠标滚轮**，移动元件为**按住鼠标中键（滚轮）进行拖动**。
5. 按照原理图进行元件的放置、连线
	1. 元件通过拖拽的方式放入原理图中，在拖拽元件时会弹出元件的参数设置界面，可以进行修改自定义的参数![[Pasted image 20231114174730.png]]
	2. 使用 *Wire* 工具进行连线![[Pasted image 20231114202944.png]]
	3. 连接完成![[Pasted image 20231114203703.png]]
***PS2*** 在连接原理图时要注意，元件与元件之间不可以通过简单的拼接实现电路的链接，而应该使用 *Wire* 进行连接
***PS3*** 如果找不到元件在哪一个库中可以通过下方的搜索框进行搜索，可以通过选中元件库进行库中搜索![[Pasted image 20231114203927.png]]
***PS4*** 如果不小心关闭 S-Edit 可以通过如下的方式恢复自己的原理图绘制：如图选择 *File > Open > Open Design* 打开自己保存的文件![[Pasted image 20231114193807.png]]如果打开保存的文件之后如图没有弹出编辑界面，可以通过右侧的 Libraries 中点击自己的库名，在下侧找到自己的文件右键 *Open View > schematic* 打开原理图![[Pasted image 20231114195107.png]]
6. 连接完成之后点击 *Check* 检查、保存![[Pasted image 20231114204403.png]]![[Pasted image 20231114204452.png]]
7. 点击 *Cell > Generate Symbols* 生成反相器的符号![[Pasted image 20231114204705.png]]![[Pasted image 20231114204936.png]]
8. 进入符号绘制界面，使用 *Path* 绘制标准的反相器符号![[Pasted image 20231114205100.png]]![[Pasted image 20231114205207.png]]![[Pasted image 20231114205218.png]]
***PS5*** 绘制反相器符号时，使用 *Path* 和线条角度变换绘制符号，也可以在 *Properties* 中编辑选中部分属性![[Pasted image 20231114205455.png]]![[Pasted image 20231114205718.png]]
9. 绘制结束后**保存**，通过 *View > Cell View > View Schematic* 返回原理图界面![[Pasted image 20231114205958.png]]
### 仿真部分
10. 放置电压源![[Pasted image 20231114210326.png]]![[Pasted image 20231114210410.png]]![[Pasted image 20231114210434.png]]
11. 放置 *Print Voltage* ![[Pasted image 20231114210618.png]]
12. 单击 *Check* 并进行**保存**
13. 在 *File > Export > Export SPICE* 导出 `.spc` 网表文件 ![[Pasted image 20231114210816.png]]
## 二、使用 T-Spice 进行仿真
14. 使用 T-Spice 打开 `.spc` 文件![[Pasted image 20231114211420.png]]
15. 修改 `.spc` 文件
	1. 通过 Edit > Insert Command 更改![[Pasted image 20231114211819.png]]
	2. 在`Files > Library file` 中输入库绝对路径，该库可以在`~\2023-2024-1EDA参考资料和软件\tanner\Libraries\Libraries\Libraries\Models\` 找到 ![[Pasted image 20231114212032.png]]
	3. 单击 *Insert Command* 插入命令，并在命令结尾加上 `tt`（无需注意大小写）![[Pasted image 20231114212536.png]]
	4. 插入瞬态分析命令![[Pasted image 20231114212828.png]]![[Pasted image 20231114212844.png]]
16. 点击 *Run Simulation* 进行仿真![[Pasted image 20231114213314.png]]
## 三、使用W-Edit 进行数据观察
17. 点击图示图标使输入输出图像分离![[Pasted image 20231114223552.png]]
18. 在 `File > Export Chart Data` 中导出图形数据![[Pasted image 20231114223637.png]]
#### 反相器的直流分析
1. 重新进行 *步骤13* 导出一个新的 `.spc` 文件
2. 修改 `.spc` 文件
	1. 修改 `VVoltageSource_2` 的值，将 `Gnd` 后的删除并加入 lib 库![[Pasted image 20231114224310.png]]
	2. 插入直流分析命令![[Pasted image 20231114224406.png]]![[Pasted image 20231114224437.png]]![[Pasted image 20231114224502.png]]
	3. 插入打印输出命令，注意与自己的端口一致![[Pasted image 20231114224734.png]]![[Pasted image 20231114224824.png]]
	4. 点击 *Run Simulation* 进行仿真![[Pasted image 20231114225000.png]]
## 四、使用 L-Edit 进行版图设计
1. 打开 L-Edit 软件，点击 *New Design* 新建设计![[Pasted image 20231114230049.png]]
***PS6*** 下方 TDB 在安装 Tanner 软件时会同步安装 Tanner Tools v16.3 ，我们需要的是其中 `Tanner Tools v16.3\Designs\Lights` 路径下的 **lights.tdb** 文件
2. 右键 Cell 区域![[Pasted image 20231114230933.png]]