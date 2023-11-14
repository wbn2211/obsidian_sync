# Tanner 软件的使用教程——以反相器电路为例
## 一、 使用 S-Edit 绘制原理图
### 原理图绘制部分
1. 打开 S-Edit 单击 `New Design` 新建一个项目![[Pasted image 20231114171725.png]]
2. 自定义项目名称和存储地点![[Pasted image 20231114171808.png]]
3. 添加存储库![[Pasted image 20231114171934.png]]
其中存储库的链接在打包下载的文件中，在路径`~\2023-2024-1EDA参考资料和软件\tanner\Libraries\Libraries\All` 下寻找文件 `All.tanner` 添加库
4. 确认全部库添加到项目中，点击 `Cell > New View` 新建原理图绘制![[Pasted image 20231114172307.png]]![[Pasted image 20231114172549.png]]
***PS1*** S-Edit 软件的放大为**直接滚动鼠标滚轮**，向上/下翻页为 **Ctrl + 滚动鼠标滚轮**，移动元件为**按住鼠标中键（滚轮）进行拖动**。
5. 按照原理图进行元件的放置、连线
	1. 元件通过拖拽的方式放入原理图中，在拖拽元件时会弹出元件的参数设置界面，可以进行修改自定义的参数![[Pasted image 20231114174730.png]]
	2. 使用 `Wire` 工具进行连线![[Pasted image 20231114202944.png]]
	3. 连接完成![[Pasted image 20231114203703.png]]
***PS2*** 在连接原理图时要注意，元件与元件之间不可以通过简单的拼接实现电路的链接，而应该使用 `Wire` 进行连接
***PS3*** 如果找不到元件在哪一个库中可以通过下方的搜索框进行搜索，可以通过选中元件库进行库中搜索![[Pasted image 20231114203927.png]]
***PS4*** 如果不小心关闭 S-Edit 可以通过如下的方式恢复自己的原理图绘制：如图选择 `File > Open > Open Design` 打开自己保存的文件![[Pasted image 20231114193807.png]]如果打开保存的文件之后如图没有弹出编辑界面，可以通过右侧的 `Libraries` 中点击自己的库名，在下侧找到自己的文件右键 `Open View > schematic` 打开原理图![[Pasted image 20231114195107.png]]
6. 连接完成之后点击 `Check` 检查、保存![[Pasted image 20231114204403.png]]![[Pasted image 20231114204452.png]]
7. 点击 `Cell > Generate Symbols` 生成反相器的符号![[Pasted image 20231114204705.png]]![[Pasted image 20231114204936.png]]
8. 进入符号绘制界面，使用 `Path` 绘制标准的反相器符号![[Pasted image 20231114205100.png]]![[Pasted image 20231114205207.png]]![[Pasted image 20231114205218.png]]
***PS5*** 绘制反相器符号时，使用 `Path` 和线条角度变换绘制符号，也可以在 `Properties` 中编辑选中部分属性![[Pasted image 20231114205455.png]]![[Pasted image 20231114205718.png]]
9. 绘制结束后**保存**，通过 `View > Cell View > View Schematic` 返回原理图界面![[Pasted image 20231114205958.png]]
### 仿真部分
10. 放置电压源![[Pasted image 20231114210326.png]]![[Pasted image 20231114210410.png]]![[Pasted image 20231114210434.png]]
11. 放置`Print Voltage` ![[Pasted image 20231114210618.png]]
12. 单击`Check` 并进行**保存**
13. 在 `File > Export > Export SPICE` 导出 `.spc` 网表文件 ![[Pasted image 20231114210816.png]]
14. 