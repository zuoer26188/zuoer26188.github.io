---
layout: post
title: 'Bugku-game'
subtitle: 'Bugku-game'
date: 2021-06-06
categories: CTF
cover: 'https://pic3.zhimg.com/v2-2555c22aed2736d1667278398885326e_r.jpg?source=1940ef5c'
tags: CTF
---
### 题目：
![](https://img-blog.csdnimg.cn/20210523203827839.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl81MDc3NDU3OQ==,size_16,color_FFFFFF,t_70)

盖楼的小游戏

让我差点忘了我是来干嘛的

fn+f12 打开网络，看到结束有个分数的php网页

score=50与sign=zMNTA===有关系，NTA===是50的base64编码

也可以查看源码，搜索sign可以找到一些蛛丝马迹
![](https://img-blog.csdnimg.cn/20210523204603902.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl81MDc3NDU3OQ==,size_16,color_FFFFFF,t_70)
可以看到右侧的 sign:zMNTA=== ，

sign为 zM + base64编码部分 + == ，

所以我们取中间的 NTA= ，用base64解码一下，果不其然,50,正好是我们玩游戏得到的分数。因此这里的sign值就是我们游戏结束后向服务器提交的分数。

可以想见，如果我们提交的分数达到了获取flag的阀值就可以获取flag。

因此要在这里做手脚

 看见：http://114.67.246.176:13124/score.php?score=50&ip=125.62.3.97&sign=zMNTA===

访问网站的score.php文件（？）（此处解读存疑，在下php没学好，麻烦大佬指点一下万分感谢）

score=50和sign=zMNTA===处分别把等号后面的改成99999和它的base64编码就好了
![](https://z3.ax1x.com/2021/06/06/2aXhcT.png)
