# latex字体与行距

[![img](https://cdn2.jianshu.io/assets/default_avatar/3-9a2bcc21a5d89e21dafc73b39dc5f582.jpg)](https://www.jianshu.com/u/5ad1f1eb8c40)

[真人找个](https://www.jianshu.com/u/5ad1f1eb8c40)关注IP属地: 江苏

2019.01.30 15:38:26字数 599阅读 12,373

# 选择字体

#### ctex宏包及其文档类自带字体

可直接使用以下六种字体：

- \songti 宋体
- \heiti 黑体
- \fangsong 仿宋
- \kaishu 楷书
- \lishu 隶书
- \youyuan 幼圆

#### 自定义字体

1. 从网上下载需要的字体
   推荐[字体口袋](http://www.zitikoudai.com/)和[求字体网](http://www.qiuziti.com/)这两个网站
2. 查找本机中的中文字体或英文字体
   快捷键`ctrl+R`调出`运行`，输入cmd。
   若要得到中文字体信息，则输入`fc-list :lang=zh`
   若要得到英文字体信息，则输入`fc-list :lang=en`
3. 在latex导言区设置如下命令



```undefined
\usepackage{xeCJK}   %中文字体
\setCJKfamilyfont{kaitibold}{Kaiti SC Bold}
\newcommand{\kaitiB}{\CJKfamily{kaitibold}}   %楷体加粗
\setCJKfamilyfont{heitibold}{Source Han Sans CN}
\newcommand{\heitiB}{\CJKfamily{heitibold}}   %黑体加粗
\setCJKfamilyfont{songtibold}{Songti SC}
\newcommand{\songtiB}{\CJKfamily{songtibold}}   %宋体加粗
```

其中，Kaiti SC Bold等是运行查找得到的所需要的字体名称。

------

# 字体大小及行距

#### 字体大小

使用命令`zihao{}`设置中文字号，例如`\zihao{-4}`为小四号。括号中的参数有16个，小号字体在前面加负号表示，如下表：

|    命令    | 大小(bp) | 意义 |
| :--------: | :------: | :--: |
| \zihao{0}  |    42    | 初号 |
| \zihao{-0} |    36    | 小初 |
| \zihao{1}  |    26    | 一号 |
| \zihao{-1} |    24    | 小一 |
| \zihao{2}  |    22    | 二号 |
| \zihao{-2} |    18    | 小二 |
| \zihao{3}  |    16    | 三号 |
| \zihao{-3} |    15    | 小三 |
| \zihao{4}  |    14    | 四号 |
| \zihao{-4} |    12    | 小四 |
| \zihao{5}  |   10.5   | 五号 |
| \zihao{-5} |    9     | 小五 |
| \zihao{6}  |   7.5    | 六号 |
| \zihao{-6} |   6.5    | 小六 |
| \zihao{7}  |   5.5    | 七号 |
| \zihao{8}  |    5     | 八号 |

#### 行距

LATEX中的行距是与字号直接相关的。

- 基本行距：在设置字号时，同时设置了基本行距为文字大小的1.2倍。
- 行距：基本行距乘上一个因子。对article等标准文档类来说，因子默认为1；对ctexart等中文文档类来说，因子默认为1.3，即行距是字号大小的![1.2\times1.3=1.56](https://math.jianshu.com/math?formula=1.2%5Ctimes1.3%3D1.56)倍。

以字号为小四号（大小为12bp）、设置20磅行距为例，说明几种方法：

1. `\zihao{-4}\linespread{1.389}\selectfont`
   其中，`\linespread{}`设置行距为基本行距的多少倍，即上面行距定义中提到的因子。此时，字号大小为`12bp`，基本行距为![12\times1.2=14.4bp](https://math.jianshu.com/math?formula=12%5Ctimes1.2%3D14.4bp)，欲设置行距为`20bp`，则`因子`为![20\div14.4\approx1.389](https://math.jianshu.com/math?formula=20%5Cdiv14.4%5Capprox1.389)。
2. `\zihao{-4}\setlength{\baselineskip}{20bp}`
   行距为`baselineskip`，这是直接设置行距的方法。
3. `\fontsize{12bp}{15.3846153846bp}\selectfont`
   命令`\fontsize{12bp}{15.3846153846bp}`设置的是字号和基本行距，对ctexart等中文文档，由于行距为基本行距的1.3倍，因此基本行距为![20\div1.3\approx15.3846153846](https://math.jianshu.com/math?formula=20%5Cdiv1.3%5Capprox15.3846153846)
4. `\zihao{-4}\setstretch{1.389}`导言区需加载宏包`\usepackage{setspace}`但是，行不通！！！！！！！
   根据刘海洋的《LATEX入门》，应该和`\zihao{-4}\linespread{1.389}\selectfont`的效果一样的啊。

最后编辑于 ：2019.01.31 15:59:15