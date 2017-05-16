# tips
useful or useless tips
# 1. notice for installing mac series os via vmware #
- close vmware service and install unlocker208 so vmware can recognize mac series os
- it is a pity that .iso may not be supported, only .cdr is supported, which should be generated from .dmg
- after setting mac vm, open vm dic and find .vmx, after `smc.present = "TRUE"` add `smc.version = 0`
- then it may be easier to finish the installation
- after getting into mac vm, it may be slow, download [beamoff](http://files.cnblogs.com/files/yipu/beamoff.zip) and install it to address the problem

# 2. 中国20大知名语料库 #
1. 中央研究院近代汉语标记语料库：http://www.sinica.edu.tw/Early_Mandarin/ ？？？
2. 中央研究院汉籍电子文献（瀚典全文检索系统）http://www.sinica.edu.tw/ftms-bin/ftmsw3 ？？？
3. 国家现代汉语语料库：http://124.207.106.21:8080/ 404
4. 国家语委现代汉语语料库：http://www.clr.org.cn/retrieval/index.html 404
5. 树图数据库：http://treebank.sinica.edu.tw/ 繁中
6. 语料库语言学在线：http://corpus4u.org 论坛
7. 北京大学中国语言学研究中心，简称CCL语料库检索系统（包括：现代汉语语料库、古代汉语语料库、汉英双语语料库）http://ccl.pku.edu.cn/Yuliao_Contents.Asp 404
8. 北京大学《人民日报》标注语料库：http://www.icl.pku.edu.cn ？？？
9. 北京语言大学的语料库：http://www.blcu.edu.cn/kych/H.htm 404
10. 清华大学的汉语均衡语料库THACorpus：http://www.lits.tsinghua.edu.cn/ainlp/source.htm ？？？
11. 山西大学语料库：http://www.sxu.edu.cn/homepage/cslab/sxuc1.htm 404
12. 台湾南岛语典藏：http://www.ling.sinica.edu.tw/Formosan/ 404
13. 闽南语典藏：http://southernmin.sinica.edu.tw/ 404
14. 香港城市大学的LIVAC共时语料库：http://www.rcl.cityu.edu.hk/livac/ ？？？ 或 http://www.LIVAC.org 繁中
15. 浙江师范大学的历史文献语料库:http://lib.zjnu.net.cn/xueke/hyywzx/xkjj.htm 404
16. 中国科学院计算所的双语语料库：http://mtgroup.ict.ac.cn/corpus/query_process.php 404
17. 中文语言资源联盟：http://www.chineseldc.org/xyzy.htm 404
18. 红楼梦汉英平行语料库：http://score.crpp.nie.edu.sg/hlm/index.htm# ？？？
19. SKETCHENGINE多语言语料库：www.sketchengine.co.uk
20. LIVAC共时语料库：http://www.livac.org/ 繁中
21. CCL汉英双语语料库检索：http://ccl.pku.edu.cn:8080/ccl_corpus/index_bi.jsp

# 3. 英语语料库 #
- http://corpus.byu.edu/

Corpus of Contemporary American English (COCA)	400 million words	1990 - 2009
Corpus of Historical American English (COHA; Summer 2009 beta)	400 million words	1810s - 2000s
BYU-BNC: British National Corpus	100 million words	1980s - 1993
TIME Corpus of American English	100 million words	1920s - 2000s
BYU-OED: Oxford English Dictionary	37 million words	1000s - 2000s
Corpus del Español	100 million words	1200s - 1900s
Corpus do Português	45 million words	1300s - 1900s

# 4. address the problem of 'urlopen error errno 10060' #
    def getUrl_multiTry(url):  
        user_agent ='"Mozilla/5.0 (Windows NT 6.2; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2125.122 Safari/537.36"'  
        headers = { 'User-Agent' : user_agent }  
        maxTryNum=10  
        for tries in range(maxTryNum):  
            try:  
                req = urllib2.Request(url, headers = headers)   
                html=urllib2.urlopen(req).read()  
                break  
            except:  
                if tries <(maxTryNum-1):  
                    continue  
                else:  
                    logging.error("Has tried %d times to access url %s, all failed!",maxTryNum,url)  
                    break  


        return html  

# 5. Ubuntu14.04（16.04も可能）とPython2でMecabを使う方法 #
1. Mecabのインストール

> sudo apt-get install mecab mecab-ipadic-utf8

2. swigとlibmecab-devのインストール

> sudo apt-get install swig

> sudo apt-get install libmecab-dev

3. mecab-python-0.996のインストール

> sudo ldconfig

# 6. cmd编译java时的坑（最近才发现） #

印象中用notepad写java是很久以前的事了，99%以上的情况都是用些workbench。最近想试试最原始的，可是忽略了一个非常微小的细节以致于运行失败。务必要记住，在写环境变量CLASSPATH的时候最后一定要加分号，像这样：

> %JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar;

最后的那个分号一定不能漏

# 7. POS-T in Chinese(Mandarin) #

|Tag|Description|Example|Tag|Description|Example|
|---|-----------|-------|---|-----------|-------|
|a|adjective|美丽|ni|organization name|保险公司|
|b|other noun-modifier|大型, 西式|nl|location noun|城郊|
|c|conjunction|和, 虽然|ns|geographical name|北京|
|d|adverb|很|nt|temporal noun|近日, 明代|
|e|exclamation|哎|nz|other proper noun|诺贝尔奖|
|g|morpheme|茨, 甥|o|onomatopoeia|哗啦|
|h|prefix|阿, 伪|p|preposition|在, 把|
|i|idiom|百花齐放|q|quantity|个|
|j|abbreviation|公检法|r|pronoun|我们|
|k|suffix|界, 率|u|auxiliary|的, 地|
|m|number|一, 第一|v|verb|跑, 学习|
|n|general noun|苹果|wp|punctuation|，。！|
|nd|direction noun|右侧|ws|foreign words|CPU|
|nh|person name|杜甫, 汤姆|x|non-lexeme|萄, 翱|

# 8. Ubuntu内的firefox装flash #
- 下载flash for linux(tar.gz)并解压
- libflashplayer.so放到usr/lib/firefox-addons/plugins

# 9. Ubuntu的一些可附加内容 #

- Launcher置于底部：

> gsettings set com.canonical.Unity.Launcher launcher-position Bottom

- 点击Luancher上的图标完成放大缩小：

> gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ launcher-minimize-window true

- JDK：

> sudo add-apt-repository ppa:webupd8team/java

> sudo apt-get update

> sudo apt-get install oracle-java8-installer 

- sublime text3：

> sudo add-apt-repository ppa:webupd8team/sublime-text-3

> sudo apt-get update

> sudo apt-get install sublime-text

- 经典菜单指示器：

> sudo add-apt-repository ppa:diesch/testing 

> sudo apt-get update 

> sudo apt-get install classicmenu-indicator

- 系统指示器SysPeek：

> sudo add-apt-repository ppa:nilarimogard/webupd8

> sudo apt-get update

> sudo apt-get install syspeek

- vim、git、vpnc、axel

- 摆放桌面图标：

> sudo cp /usr/share/applications/*.desktop ~/桌面

> cd ~/桌面

> sudo chown 当前登录用户 *.desktop

> chmod a+x *.desktop

# 10. ubuntu下装crfsuite #

- 从github的chokkann上把liblbfgs和crfsuite弄下来

- apt装libtool、m4、automake、autoconf（如果没装的话）

- 装liblbfgs

> cd liblbfgs   

> ./autogen.sh  

> ./configure  

> make && make install

- 装crfsuite

> cd crfsuite

> ./autogen.sh  

> ./configure  

> make && make install  

- 装python-dev或python3-dev（如果没装的话）

- 装crfsuite-python

> cd swig/python/  

> ./prepare.sh  

> python setup.py build_ext --include-dir=/usr/local/include --library-dirs=/usr/local/lib -R /usr/local/lib  

> python setup.py install

# 11. 日语语料库 #

- 国会会議検索システム：http://kokkai.ndl.go.jp

- 茶漉一般公開サイト：http://telldev.cla.purdue.edu/chakoshi/public.html

# 12. boost依赖、安装、环境变量 #

mpi-default-dev libicu-dev python-dev python3-dev libbz2-dev zlib1g-dev

./bootstrap.sh --with-toolset=clang
	
./b2 install --build-type=complete --layout=versioned threading=multi --prefix="/usr/lib/boost-1.60"

export C_INCLUDE_PATH=/usr/lib/boost-1.60/include/boost-1_60:$C_INCLUDE_PATH

export CPLUS_INCLUDE_PATH=/usr/lib/boost-1.60/include/boost-1_60:$CPLUS_INCLUDE_PATH

export LD_LIBRARY_PATH=/usr/lib/boost-1.60/lib:$LD_LIBRARY_PATH

export LIBRARY_PATH=/usr/lib/boost-1.60/lib:$LIBRARY_PATH

# 13. 如何让win的cmd能够运行linux终端的一些常用指令 #

- Cygwin:http://www.cygwin.com/

- 设置环境变量

# 14. win下python2与3共存以及pip、pip3的设置 #

- 安装python2、python3

- 检查4个环境变量

- 进到python3下目录，python.exe更名为python3.exe

- 删除python3下script下的pip.exe

- 用户文件夹下新建pip文件夹，pip下新建pip.ini，添加：

    [global]
    
    index-url=http://pypi.douban.com/simple
    
    trusted-host=pypi.douban.com
    
    disable-pip-version-check=true
    
    timeout=120

- 输入`python -V` `python3 -V` `pip -V` `pip3 -V` 测试

- 如果pip3有问题，则`python3 -m pip install -U pip`

# 15. win10下配置tensorflow #

- http://blog.csdn.net/sb19931201/article/details/53648615

# 16. 重要的 #

- A搜索算法——图形搜索算法，从给定起点到给定终点计算出路径。其中使用了一种启发式的估算，为每个节点估算通过该节点的最佳路径，并以之为各个地点排定次序。算法以得到的次序访问这些节点。因此，A*搜索算法是最佳优先搜索的范例。

- 集束搜索（又名定向搜索，Beam Search）——最佳优先搜索算法的优化。使用启发式函数评估它检查的每个节点的能力。不过，集束搜索只能在每个深度中发现最前面的m个最符合条件的节点，m是固定数字——集束的宽度。
　　
- 二分查找（Binary Search）——在线性数组中找特定值的算法，每个步骤去掉一半不符合要求的数据。
　　
- 分支界定算法（Branch and Bound）——在多种最优化问题中寻找特定最优化解决方案的算法，特别是针对离散、组合的最优化。

- Buchberger算法——一种数学算法，可将其视为针对单变量最大公约数求解的欧几里得算法和线性系统中高斯消元法的泛化。
　　
- 数据压缩——采取特定编码方案，使用更少的字节数（或是其他信息承载单元）对信息编码的过程，又叫来源编码。
　　
- Diffie-Hellman密钥交换算法——一种加密协议，允许双方在事先不了解对方的情况下，在不安全的通信信道中，共同建立共享密钥。该密钥以后可与一个对称密码一起，加密后续通讯。
　　
- Dijkstra算法——针对没有负值权重边的有向图，计算其中的单一起点最短算法。
　　
- 离散微分算法（Discrete differentiation）

- 动态规划算法（Dynamic Programming）——展示互相覆盖的子问题和最优子架构算法

- 欧几里得算法（Euclidean algorithm）——计算两个整数的最大公约数。最古老的算法之一，出现在公元前300前欧几里得的《几何原本》。

- 期望-最大算法（Expectation-maximization algorithm，又名EM-Training）——在统计计算中，期望-最大算法在概率模型中寻找可能性最大的参数估算值，其中模型依赖于未发现的潜在变量。EM在两个步骤中交替计算，第一步是计算期望，利用对隐藏变量的现有估计值，计算其最大可能估计值；第二步是最大化，最大化在第一步上求得的最大可能值来计算参数的值。

- 快速傅里叶变换（Fast Fourier transform，FFT）——计算离散的傅里叶变换（DFT）及其反转。该算法应用范围很广，从数字信号处理到解决偏微分方程，到快速计算大整数乘积。

- 梯度下降（Gradient descent）——一种数学上的最优化算法。

- 哈希算法（Hashing）

- 堆排序（Heaps）

- Karatsuba乘法——需要完成上千位整数的乘法的系统中使用，比如计算机代数系统和大数程序库，如果使用长乘法，速度太慢。该算法发现于1962年。

- LLL算法（Lenstra-Lenstra-Lovasz  lattice reduction）——以格规约（lattice）基数为输入，输出短正交向量基数。LLL算法在以下公共密钥加密方法中有大量使用：背包加密系统（knapsack）、有特定设置的RSA加密等等。

- 最大流量算法（Maximum flow）——该算法试图从一个流量网络中找到最大的流。它优势被定义为找到这样一个流的值。最大流问题可以看作更复杂的网络流问题的特定情况。最大流与网络中的界面有关，这就是最大流-最小截定理（Max-flow min-cut theorem）。Ford-Fulkerson 能找到一个流网络中的最大流。

- 合并排序（Merge Sort）

- 牛顿法（Newton's method）——求非线性方程（组）零点的一种重要的迭代法。

- Q-learning学习算法——这是一种通过学习动作值函数（action-value function）完成的强化学习算法，函数采取在给定状态的给定动作，并计算出期望的效用价值，在此后遵循固定的策略。Q-leanring的优势是，在不需要环境模型的情况下，可以对比可采纳行动的期望效用。

- 两次筛法（Quadratic Sieve）——现代整数因子分解算法，在实践中，是目前已知第二快的此类算法（仅次于数域筛法Number Field Sieve）。对于110位以下的十位整数，它仍是最快的，而且都认为它比数域筛法更简单。

- RANSAC——是“RANdom SAmple Consensus”的缩写。该算法根据一系列观察得到的数据，数据中包含异常值，估算一个数学模型的参数值。其基本假设是：数据包含非异化值，也就是能够通过某些模型参数解释的值，异化值就是那些不符合模型的数据点。

- RSA——公钥加密算法。首个适用于以签名作为加密的算法。RSA在电商行业中仍大规模使用，大家也相信它有足够安全长度的公钥。

- Schönhage-Strassen算法——在数学中，Schönhage-Strassen算法是用来完成大整数的乘法的快速渐近算法。其算法复杂度为：O(N log(N) log(log(N)))，该算法使用了傅里叶变换。

- 单纯型算法（Simplex Algorithm）——在数学的优化理论中，单纯型算法是常用的技术，用来找到线性规划问题的数值解。线性规划问题包括在一组实变量上的一系列线性不等式组，以及一个等待最大化（或最小化）的固定线性函数。

- 奇异值分解（Singular value decomposition，简称SVD）——在线性代数中，SVD是重要的实数或复数矩阵的分解方法，在信号处理和统计中有多种应用，比如计算矩阵的伪逆矩阵（以求解最小二乘法问题）、解决超定线性系统（overdetermined linear systems）、矩阵逼近、数值天气预报等等。

- 求解线性方程组（Solving a system of linear equations）——线性方程组是数学中最古老的问题，它们有很多应用，比如在数字信号处理、线性规划中的估算和预测、数值分析中的非线性问题逼近等等。求解线性方程组，可以使用高斯—约当消去法（Gauss-Jordan elimination），或是柯列斯基分解（ Cholesky decomposition）。

- Strukturtensor算法——应用于模式识别领域，为所有像素找出一种计算方法，看看该像素是否处于同质区域（ homogenous region），看看它是否属于边缘，还是是一个顶点。

- 合并查找算法（Union-find）——给定一组元素，该算法常常用来把这些元素分为多个分离的、彼此不重合的组。不相交集（disjoint-set）的数据结构可以跟踪这样的切分方法。合并查找算法可以在此种数据结构上完成两个有用的操作：

- 查找：判断某特定元素属于哪个组。

- 合并：联合或合并两个组为一个组。

- 维特比算法（Viterbi algorithm）——寻找隐藏状态最有可能序列的动态规划算法，这种序列被称为维特比路径，其结果是一系列可以观察到的事件，特别是在隐藏的Markov模型中。

# 17. kali源 #

	#中科大kali源
	deb http://mirrors.ustc.edu.cn/kali sana main non-free contrib
	deb http://mirrors.ustc.edu.cn/kali-security/ sana/updates main contrib non-free
	deb-src http://mirrors.ustc.edu.cn/kali-security/ sana/updates main contrib non-free
	#阿里云kali源
	deb http://mirrors.aliyun.com/kali sana main non-free contrib
	deb http://mirrors.aliyun.com/kali-security/ sana/updates main contrib non-free
	deb-src http://mirrors.aliyun.com/kali-security/ sana/updates main contrib non-free

# 18. 中文分词参考 #

- 中文分词工具探析：http://www.cnblogs.com/en-heng/p/6225117.html

- 中文分词算法总结：http://blog.csdn.net/baidu_15113429/article/details/70048945

# 19. 页面定界 #

	[].forEach.call($$("*"),function(a){a.style.outline="1px solid #"+(~~(Math.random()*(1<<24))).toString(16)})

# 20. 搜索引擎汇总 #

http://www.sowang.com/link.htm

http://www.jianshu.com/p/ae7c8513bb00


