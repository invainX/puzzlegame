# -徽章
![](https://img.shields.io/badge/{language}-{python}-{yellowgreen}.svg)
![](https://img.shields.io/badge/{build}-{passed}-{yellowgreen}.svg)

# -运行环境
- 操作系统：Windows
- python版本：3.8以上
- 游戏实现依赖参照requirementx.txt

# -编译方法
- 安装依赖requirements.txt后运行puzzlegame.py

# -游戏使用方法
- 直接运行puzzlegame.py
若无法运行，需要先下载无框字符.zip，再手动修改一下代码里的路径为本地路径即可运行

# -AI使用方法
- 1、运行request.py获取题目并加载图片。具体题目需在代码中修改
- 2、从接口获取图片后运行division.py切割图片为9块碎片，此部分为
- 3、运行distinguish.py识别碎片属于哪个字母，distinguish.py中的路径也需要改为本地路径
- 4、运行speed_distinguish.py实现题目碎片与已有碎片的一一对应，可得到对应的数字序列，少数图片可能识别不出来需要人为检验一下。同样需要修改路径。
- 5、在Astar.py将所得序列中的八个数每个数加1输入，缺少的那个数即空白格序列为0，并输入目标序列，且0为空白格，运行后得到操作步骤。
- 6、在双向bfs.py先指明空白格，将所得序列中的八个数每个数加1输入，空白格对应序列数也需输入，并输入目标序列，运行后得到操作步骤与 Astar.py比较得出最优解。
如：空白格：7   初始序列：9 8 7 6 5 4 3 2 1 ，  目标序列：1 2 3 4 5 6 7 8 9
- 7、运行send.py发送解法并返回当前排名
- 李志炜负责2、3、4部分 李赫负责1、5、6、7部分
## -说明：
- 若初始序列有解，则强制交换以后将其交换回来，即相当于无交换，上述方法得到的步骤可直接使用。
- 若初始序列无解，则将目标序列中的需强制交换的位置先进行交换，再在强制交换后将目标序列换回。
例如：初始序列为（1，2，3，5，4，0，7，8，9），此时无解，在第五步后强制交换第七位和第八位，则先设置目标序列为（1,2,3,4,5,0,8,7,9),运行Astar.py或双向bfs.py记录前五步，再把目标序列设置为（1，2，3，4，5，0，7，8，9）后运行Astar.py或双向bfs.py得到走法。
