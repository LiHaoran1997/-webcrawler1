# -webcrawler1


使用步骤：
1.安装python 3.5（别的可能有bug，尤其是3.7，不知道下载修复没有）
2.安装python IDE（我用的是pycharm，大神随意嘿嘿嘿）
3.安装scrapy（具体自行百度）
4.在main函数中已经编写好执行文件，只需要run一下就ok了！


爬取其他网站开发大致步骤：
1.命令行中输入scrapy genspider abc(网站名称)  www.abc.com
1.1 使用scrapy的crawlspider模板也可以，即 scrapy genspider -t crawlspider abc www.abc.com

2.分析网站的url结构以及按F12或者右键“审查元素”进入网页html/css代码页面，分析爬取字段以及找到爬取字段的css/xpath路径。
3.在spider文件中的abc.py(具体看网站名称)里面编写parse函数或者parse_detail函数（crawlspider不允许重写parse函数，还要设置爬取规则（Rules））。
4.如果是动态网页，需要在middlewares中编写中间件，比如模拟登录（也可以写在spiders里面），鼠标自动下拉等等等。
5.pipelines里面已经写好mysql同步以及异步的代码，如果用同步做测试需要改一下sql语句以及相关设置，异步直接移步items。
6.items将传递过来参数field一下，然后如果使用异步的话需要写一下插入数据库的代码（复制一下上面我写过的就好啦）
7.settings里面把pipelines启动一下。
8.Run！
