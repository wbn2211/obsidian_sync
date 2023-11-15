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
	1. 通过 *Edit > Insert Command* 更改![[Pasted image 20231114211819.png]]
	2. 在 *Files > Library file* 中输入库绝对路径，该库可以在`~\2023-2024-1EDA参考资料和软件\tanner\Libraries\Libraries\Libraries\Models\` 找到 ![[Pasted image 20231114212032.png]]
	3. 单击 *Insert Command* 插入命令，并在命令结尾加上 `tt`（无需注意大小写）![[Pasted image 20231114212536.png]]
	4. 插入瞬态分析命令![[Pasted image 20231114212828.png]]![[Pasted image 20231114212844.png]]
16. 点击 *Run Simulation* 进行仿真![[Pasted image 20231114213314.png]]
## 三、使用W-Edit 进行数据观察
17. 点击图示图标使输入输出图像分离![[Pasted image 20231114223552.png]]
18. 在 *File > Export Chart Data* 中导出图形数据![[Pasted image 20231114223637.png]]
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
2. 右键 Cell 区域 *New* 新建单元，并命名 `PMOS` ![[Pasted image 20231114230933.png]]
3. 按照表格绘制
	1. 绘制 *N Well* ![[Pasted image 20231114233005.png]]
		1. 首先选中 *N Well* 
		2. 选择 *Box* 绘制
		3. 画个框
		4. 点击 *Edit Project(s)* 修改属性![[Pasted image 20231114233253.png]]
	2. 绘制 *Active* ![[Pasted image 20231114233432.png]]
	3. 绘制 *P Select* ![[Pasted image 20231114233508.png]]
	4. 绘制 *Poly* ![[Pasted image 20231114233541.png]]
	5. 绘制 *Active Contact* ![[Pasted image 20231114233637.png]]![[Pasted image 20231114233616.png]]
	6. 绘制 *Metal 1* ![[Pasted image 20231114233706.png]]![[Pasted image 20231114233718.png]]

| N Well  | Active | P Select | Poly  | Active Contact | Metal 1 |
| ------- | ------ | -------- | ----- | -------------- | ------- |
| 24 * 15 | 14 * 5 | 18 * 9   | 2 * 9 | 2 * 2          | 4 * 4   |
4. 点击 *tool > DRC* 进行 DRC 检查，在中间下部 *Verification Navigator* 显示 `0 errors` 为正确，否则根据相关提示进行改正![[Pasted image 20231114233948.png]]
5. 右键 Cell 区域 *New* 新建单元，并命名 `NMOS` ，根据表格绘制，并进行 *DRC* 检测和**保存**

| Active | N Select | Poly  | Active Contact | Metal 1 |
| ------ | -------- | ----- | -------------- | ------- |
| 14 * 5 | 18 * 9   | 2 * 9 | 2 * 2          | 4 * 4   | 
6. 右键 Cell 区域 *New* 新建单元，并命名 `Basecontact_P` ，根据表格绘制，并进行 *DRC* 检测和**保存**

| N Well  | Active | N Select | Active Contact | Metal 1 |
| ------- | ------ | -------- | -------------- | ------- |
| 15 * 15 | 5 * 5  | 9 * 9    | 2 * 2          | 4 * 4   |
7. 右键 Cell 区域 *New* 新建单元，并命名 `Basecontact_N` ，根据表格绘制，并进行 *DRC* 检测和**保存**

| Active | P Select | Active Contact | Metal 1 |
| ------ | -------- | -------------- | ------- |
| 5 * 5  | 9 * 9    | 2 * 2          | 4 * 4   |
8. 右键 Cell 区域 *New* 新建单元，并命名 `Port A` ，根据表格绘制，并进行 *DRC* 检测和**保存**

| Poly Contact | Poly  | Metal 1 | Via   | Metal 2 |
| ------------ | ----- | ------- | ----- | ------- |
| 2 * 2        | 5 * 5 | 10 * 4  | 2 * 2 | 4 * 4   |
9. 右键 Cell 区域 *New* 新建单元，并命名 `Out` ，根据表格绘制，并进行 *DRC* 检测和**保存**

| Metal 2 | Via   |
| ------- | ----- |
| 4 * 4   | 2 * 2 | 
***PS7*** 在新建单元时要注意，单元的命名中是不能含有中文和空格的，尽量使用英文进行命名
10. 右键 Cell 区域 *New* 新建单元，并命名 `inv`，点击 Cell > Instance 引入 `PMOS` 和 `NMOS`,通过 *Draw > Align >* 进行对齐![[Pasted image 20231115000517.png]]![[Pasted image 20231115000810.png]]
11. 引入 `Basecontact_N` 和 `Basecontact_P` 单元，用 Poly 将栅极连接![[Pasted image 20231115001118.png]]
12. 引入 `Port_A` 作为输入端口，与 Poly 相接，并绘制 Metal 1 将漏极连接起来![[Pasted image 20231115143235.png]]
13. 引入 `Out` 作为输出端口，放置在 Metal 1 上![[Pasted image 20231115143324.png]]
14. 进行 *DRC* 检查，**保存**
15. 使用 Metal 1 绘制电源线和地线，将 `Basecontact_P` 和 `PMOS` 的源极相连，`Basecontact_N` 和 `NMOS` 的源极相连![[Pasted image 20231115143948.png]]
16. 使用 *Box Port* 工具通过框选定义端口 `Vdd` 、 `Gnd` 、 `In` 、 `Out` 。其中 `In` 和 `Out` 定义在 Metal 2 层![[Pasted image 20231115144109.png]]![[Pasted image 20231115144544.png]]
17. 进行 *DRC* 检查并**保存**
## 五、使用 LVS 进行电路图与版图对比
1. 提取版图的 `.spc` 文件
	1. 在 L-Edit 软件中打开 *Tools > Extract Setup* 来设置导出文件![[Pasted image 20231115144929.png]]
	2. 设置 Lights.ext 的路径，该文件位于 `Tanner Tools v16.3\Designs\Lights` ，该文件安装 Tanner 时已经安装， SPICE extract output file 可以自定义输出的文件路径和文件名 ![[Pasted image 20231115145332.png]]
	3. 设置结束后点击 *Tools > Extract* 进行导出，如果报错请检查前一步的导出设置和版图的 DRC 检测是否通过![[Pasted image 20231115150035.png]]
	4. 