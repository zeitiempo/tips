# tips
useful or useless tips
# 1. notice for installing mac series os via vmware #
- close vmware service and install unlocker208 so vmware can recognize mac series os
- it is a pity that .iso may not be supported, only .crf is supported, which should be generated from .dmg
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

# 12. boost依赖、安装、环境变量 #

mpi-default-dev libicu-dev python-dev python3-dev libbz2-dev zlib1g-dev

./bootstrap.sh --with-toolset=clang
	
./b2 install --build-type=complete --layout=versioned threading=multi --prefix="/usr/lib/boost-1.60"

export C_INCLUDE_PATH=/usr/lib/boost-1.60/include/boost-1_60:$C_INCLUDE_PATH

export CPLUS_INCLUDE_PATH=/usr/lib/boost-1.60/include/boost-1_60:$CPLUS_INCLUDE_PATH

export LD_LIBRARY_PATH=/usr/lib/boost-1.60/lib:$LD_LIBRARY_PATH

export LIBRARY_PATH=/usr/lib/boost-1.60/lib:$LIBRARY_PATH
