# 文档
    ```bash
    npm i docsify-cli -g
    docsify init ./docs
    Set-ExecutionPolicy RemoteSigned
    ```

  1. cmd、npm和git代理设置与清除  
    ```bash
    set http_proxy=http://proxy.yourname.com:8080
    set http_proxy_user=
    set http_proxy_pass=
    eg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyEnable /t REG_DWORD /d 0 /f

    npm config set proxy=http://proxy.yourname.com:8080
    npm config delete proxy

    git config --global http.proxy http://proxy.yourname.com:8080
    git config –global http.proxy http://user:password@http://proxy.yourname.com:8080
    git config –get –global http.proxy
    git config --system (或 --global 或 --local) --unset http.proxy
  ```

# Git
  > 更新添加私钥位置  
  ```bash
  exec ssh-agent bas
  eval ssh-agent -s
  ssh-add "window 私钥路径位置"
  ```

  ## 基本  
    ```bash
    git config --global user.name "bo.wen"
    git config --global user.email "bo.wen@kunlun-inc.com"
    cat ~\.gitconfig

    git init  初始化空仓库
    git status
    git add README.MD
    git rm --cache README.MD
    git add -A

    git remote -v
    git push origin master
    git pull origin master
    git push origin master -u
    git clone https://xxx aabbcc
    ```

## 分支

```bash
git checkout test1 切换分支
git checkout -b test1 创建并切换分支
git branch -d test1 删除分支

git merge test1 --no-ff 把test1合并到master  --no-ff 便于log 查看
git push origin test1  把分支推到远端
git push origin test1:f1  把分支推到远端叫f1
git push origin :test1  从本地把分支从远端删除
```

## 合并
```bash
git log
git log --oneline
git log --oneline -3
git show 2ab1123
git dog

master 合并分支
git co master
git merge test1 前提是没有冲突
git merge test1 --no-ff 把test1合并到master  --no-ff 便于log 查看

master更新的时候分支需要合并master
git pull
git co test1
git merge master  git rebase maseter  merge是合并操作，默认不会提交合并中修改内容，关注的是历史操作; rebase是没有合并操作的，只是将当前分支所作的修改复制到目标；关注开发过程;（rebase黄金法则，绝对不要再公共分支使用rebase例如master）

如果出现冲突  <<<<< 当前     >>>>需要合并的
git mergetool

```
  * 自己和别人合并，差距较大
  * git 自己的仓库
  * git clone https://github.com/ritaswc/wechat_app_template.git
  * git remote -v 查看远程有几个分支
  *   origin  git@10.5.100.25:/home/git/repos/static.dc2.kunlun.com.git (fetch)
  *   origin  git@10.5.100.25:/home/git/repos/static.dc2.kunlun.com.git (push)
  *   origin 是远程连接
  * 添加上游仓库   upstream可以随便写，如aa，bb 
  * git remote add upstream https://github.com/ritaswc/wechat_app_template.git
  * 将 upstream下的代码拉到本地。默认拉master 可以在追加列入git fetch upstream 分支； pull = fetch + merge，pull会做自动合并，多人协作pull比较多， fetch是同步上游仓库比较多
  * git fetch upstream
  * 如果是做了贡献用 merge 否则用rebase
  * git rebase upstream/master
  * 将代码更新到自己的仓库
  * git push
  * git log

## 回滚撤销  
一般 master 使用 revert ； 自己的 使用reset

```bash
$ git reset master^  每一个^符号表示前一次
git reset master~5  相对撤销
git reset 2ab1123   绝对撤销
git reset --hard
git reset --hard HEAD
git reset --hard HEAD^
git reset --soft

git reflog

git revert 撤销某次操作，此次操作之前和之后的commit和history 都会保留，并且把这次撤销作为最近一次提交。
git revert HEAD~2 //撤销到倒数第二次
git revert 2ab1123   绝对撤销
```
##  gitignore和 fork
> [gitignore](https://www.toptal.com/developers/gitignore "gitignore 生成") 根目录下.gitignore 配制文件

```vim
*.sh
# 忽略 .settings 目录下所有文件
.settings/

# 以下表示以 .txt结尾的文件是不能被忽略的
!*.txt
# a目录下所有的.class 是不上传的
/a/*.class
```
# Html
## demo
  ### imput 反选
  ```html
  <!doctype html>
  <html>
  <head>
  <meta charset="utf-8">
  <title>无标题文档</title>
  <script type="text/javascript">
  function selectAll(){
    var form2 = document.forms['form2'];
    for(var i=0;i<form2.length;i++)
      {
        var e = form2.elements[i];
        if(e.type == "checkbox"){
          e.checked = true;
          }
        }
    }
  </script>
  </head>
  <body>
    <form id="form2" name="bobo" method="post" action="">
    <input type="checkbox" name="cd" value="1" />
    <input type="checkbox" name="cd" value="2" />
    <input type="checkbox" name="cd" value="3" />
    <a href="" >1111</a>
    <input type="button" name="btn" onClick="selectAll()" value="submit" />
    </form>
  </body>
  </html>
  ```
<!-- js start-->
# Js

  ```js
  //判断手机横屏  竖屏
  (function rotate(){
    var orientation=window.orientation;
    if(orientation==90||orientation==-90){
        document.body.style.display='none';
        alert("请使用竖屏访问！");
    }
    window.onorientationchange=function(){
        document.body.style.display="block";
        rotate();
    };
  })()
  ```
  ## 语法
  1. 字符串：sXXX，如：sName，sHtml；
  2. 数字：nXXX，如：nPage，nTotal；
  3. 逻辑：bXXX，如：bChecked，bHasLogin；
  4. 数组：aXXX，如：aList，aGroup；
  5. 正则：rXXX，如：rDomain，rEmail；
  6. 函数：fXXX，如：fGetList；
  7. DOM节点：dXX，如：dDiv，dSpan；
  8. 其他类型：oXXX，如：oButton，oDate；
### console 
1. console.table()  
  对于某些复合类型的数据，console.table方法可以将其转为表格显示。
  ```js
  var languages = [
    { name: "JavaScript", fileExtension: ".js" },
    { name: "TypeScript", fileExtension: ".ts" },
    { name: "CoffeeScript", fileExtension: ".coffee" }
  ];
  console.table(languages);
  ```
2. console.count()
  count方法用于计数，输出它被调用了多少次。可以接受一个字符串作为参数，作为标签，对执行次数进行分类。
  ```js
  function greet(user) {
      console.count(user);
      return "hi " + user;
    }
    greet('bob')
    // bob: 1
    // "hi bob"
    greet('alice')
    // alice: 1
    // "hi alice"
    console.log(greet('bob'))
    // bob: 2
    // "hi bob"
  ```
3. console.assert()
  方法主要用于程序运行过程中，进行条件判断，如果不满足条件，就显示一个错误，但不会中断程序执行。这样就相当于提示用户，内部状态不正确  
  `console.assert(false, '判断条件不成立')`
4. console.time()，console.timeEnd() 计时
  ```js
  console.time('Array initialize');
  var array= new Array(1000000);
  for (var i = array.length - 1; i >= 0; i--) {
    array[i] = new Object();
  };
  console.timeEnd('Array initialize');
  // Array initialize: 1914.481ms
  ```
5. console.group()，console.groupEnd()，console.groupCollapsed() 信息分组
      ```js
      console.group('一级分组');
      console.log('一级分组的内容');

      console.group('二级分组');
      console.log('二级分组的内容');

      console.groupEnd(); // 二级分组结束
      console.groupEnd(); // 一级分组结束
      ```    
6. console.dir() console.dirxml() 打印对象、数组  

### 控制台命令
  1. keys(object)，values(object) 返回数组
  2. copy(object)：复制特定 DOM 元素到剪贴板。
  3. debugger 语句
  ```js
  for(var i = 0; i < 5; i++){
    console.log(i);
    if (i == 2) debugger;
  }
  // Chrome 浏览器中，当代码运行到debugger语句时，就会暂停运行，自动打开脚本源码界面
  ```

## funciton
  ### 获取url参数
  ```js
  function getUrlPara()
  {
    var url = document.location.toString();
    var arrUrl = url.split("?");
    var para = arrUrl[1];
    return para;
  }
  function getUrlParam(name)  
  {  
    var reg = new RegExp("(^|&)"+ name +"=([^&]*)(&|$)");  
    var r = window.location.search.substr(1).match(reg);  
    if (r!=null) return unescape(r[2]); return null;  
  }
  ```
  ### get write cookie
  ```js
  function jumpPC(){
    writeCookie('koramgame_jp','1',1);
    location.href = 'http://www.koramgame.co.jp'
    }
  function writeCookie(cookieName,cookieValue,nDays)
  {
    var today = new Date();
    var expire = new Date();
    if (nDays==null || nDays==0) nDays=1;
    expire.setTime(today.getTime() + 8640000*nDays);
    document.cookie = cookieName+"="+escape(cookieValue) + ";domain=.koramgame.co.jp;path=/";
  }

  function getCookieVal(offset) { 
    var endstr = document.cookie.indexOf (";", offset); 
    if (endstr == -1) endstr = document.cookie.length; 
    return unescape(document.cookie.substring(offset, endstr)); 
  } 
  function getCookie(name) {
      var arg = name + "="; 
      var alen = arg.length; 
      var clen = document.cookie.length; 
      var i = 0; 
      while (i < clen) { 
        var j = i + alen; 
        if (document.cookie.substring(i, j) == arg) return getCookieVal (j); 
        i = document.cookie.indexOf(" ", i) + 1; 
        if (i == 0) break; 
      } 
    return null; 
  }
  ```
## Array 对象  
  ### reduce()  
  将数组元素计算为一个值（从左到右）。
  ```js
  // 示例1
  const calendarTypeOptions = [
  { key: 'CN', display_name: 'China' },
  { key: 'US', display_name: 'USA' },
  { key: 'JP', display_name: 'Japan' },
  { key: 'EU', display_name: 'Eurozone' }
  ]

  // arr to obj, such as { CN : "China", US : "USA" }
  const calendarTypeKeyValue = calendarTypeOptions.reduce((acc, cur) => {
    acc[cur.key] = cur.display_name
    return acc
  }, {})
  ```
# 账号
!> 123
## 代理
?> 456
- [ ] foo
- [x] baz
- [] bam <~ not working

ip|节点|###
:-|:-:|-:
10.7.6.174|市场|cde
10.45.170.117|bcd|cde
10.22.246.11|bcd|cde
10.22.105.254:3128|香港
10.22.90.254:3128|香港
10.22.246.254:3128|台湾
10.22.58.254:3128|韩国
10.22.126.254:3128|韩国
10.22.174.254:3128|美国
10.22.29.254:3128|泰国

## kl-账号
  project|username|password|ext
  :-|:-:|:-:|:-
  禅道|bo.wen|Bo123456|10.4.250.2 project.cd.kunlun.work
  手机vpn账号密码|overseas|KL27hw68
  pc vpn|support|sp111PL18
  京东支付密码|###|Bob.wen0917
  cnzz|hongkang1999@163.com|84519447
  cnzz|nana07@tom.com|89703718
  百度统计|dakunlunpc|wb407567
  百度统计wap|dakunlunwap|wb407567
  vk账号|8613601316493|19881001luyang|卢杨
  twitter|daijin0731|daijin208630|代金
  合服|webmaster|mimafuzabuhaoji
  越南账号1|czucg0|cz89631139
  越南账号2|k1ds222|111111
  马康fb|sgravity@163.com|makang315
  谷文义|kevin1007@outlook.com|Gu@667788
  svn|wenbo|reoioi349034|svn://10.4.250.31/dmp/fmp.kunlun.com

# Linux
  磁盘空间查询
  $`du -sh * | sort -nr | head`
  ```
  ps -ef |grep rsync |grep -v grep |grep cms |awk '{print $2}'|xargs kill -9
  ps -ef |grep -v grep |grep start_web |awk '{print $2}'|xargs kill -9
  ```
  ngnix 返回404
  `server { listen 80 default; server_name _; return 404; }`
  一个文件去掉重复的行
  ```
  sort file |uniq
  grep '"GET http://jhzr.kunlun.com/? HT' lighttpd-access-jhzr-20160807.log |awk '{print $1}'| sort -u |wc -l
  ```
  取出两个文件的并集(重复的行只保留一份)
  $`cat file1 file2 | sort | uniq > file3`

## find
  ```bash
  find . -name "*.html" -type f |xargs grep "####" |wc -l
  find . -name "*.html" -type f |xargs sed -i -e 's/##/##/g'
  find . -name "*.html"|xargs grep -l "href=\"/pay\""
  find . -type f -name "*.html"|xargs sed -i -e "s/<title\s*.*title>/<title>TERA 神谕之战 中国官方网站--高清狠动作MMORPG<\/title>/g"
  find . -type f -name "*.html"|xargs sed -i -e "s/<meta\s*name=\"keywords\".*>/<meta name=\"keywords\" content=\"TERA,TERA OL,TERA官网,TERA官方网站,TERA国服,放逐者,TERA首测,TERA二测，TERA测试，TERA激活码,TERA下载,全场景无锁定,性感人设, TERA种族，TERA职业，TERA图片，TERA视频，TERA新闻，3D网游,韩游,客户端网游,免费网游,真致，真游戏，期待网游，动作网游，天堂3，世界级制造，极尽真实，狠动作，4K高清，神谕，神谕之战\" \/>/g"
  find . -type f -name "*.html"|xargs sed -i -e "s/<meta\s*name=\"description\".*>/<meta name=\"description\" content=\"高清狠动作网游《TERA》,中文名《神谕之战》，是由韩国顶尖团队Bluehole Studio历时6年，不间断研发优化，耗资5亿人民币打造的世界级MMO。游戏采用>次世代Unreal Engine 3引擎，还原4K高清画质，史上最大无缝地图，纳米微纹理，不设限魔幻世界，多层级立体还原。真实无锁定打击，动态物理碰撞还原，怪物BOSS不定向判定，华丽连招感受技术>流操作极致，是一款划时代的网游巨作。国服独有6大特色系统百人团队历经2年研发而成，2014暑期档火爆公测！敢做狠角色，等你来挑战！\" \/> /g"

  ```
## scp
  ```bash
  scp -P7710 /data/app/conf/rsyncd.05.secrets longfei.huo@item.kunlun.com:/tmp/
  ```

# windows
## 常用命令
{% page-ref page="about/terminology.md" %}
```bash
# F7 cmd 历史命令

```



