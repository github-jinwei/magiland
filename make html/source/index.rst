.. magiland documentation master file, created by
   sphinx-quickstart on Mon Nov 27 23:58:49 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to magiland's documentation!
====================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:



API v2.2
==================

* :ref:`LatestVersion 版本更新`
* :ref:`MagicDeviceSignIn 设备号登陆`
* :ref:`MagicPuller 获取场景列表`
* :ref:`MagicRegister 手机号码及VIP码登录`
* :ref:`MagicBonder 设备号与手机号码绑定`
* :ref:`MagicValidate 验证号码`
* :ref:`MagicCharger 用户付款服务`
* :ref:`MagicDLRecorder 手机号码关联深度链接ID`
* :ref:`Feedback 用户反馈`
* :ref:`Event 打点事件`

###LatestVersion

**url:** http://HOSTNAME/BlingoServlet/LatestVersion?

**method:** GET

+--------+------+------------+
| params | type | desc       |
+========+======+============+
| ctype  | char | 客户端类型 |
+--------+------+------------+

**rtype:** string

**return:** 成功返回

::

    1.6:0 # 是否强制更新（0否/1是）

###MagicDeviceSignIn

**url:** http://HOSTNAME/BlingoServlet/MagicDeviceSignIn?

**method:** GET

+--------+--------+--------------------+
| params | type   | desc               |
+========+========+====================+
| dd     | string | (加密)设备号       |
+--------+--------+--------------------+
| dl     | string | (非必传)深度链接ID |
+--------+--------+--------------------+

**rtype:** json

**return:** 成功返回

::

    {
        bid = 20925; #必果ID
        did = b91779aef15a4b2f8606826c7910e3fb; #设备ID
        dl = 097; #深度链接ID
        pho = ""; #电话号码
        reg = "Tue Nov 21 18:33:05 CST 2017"; #第一次登录时间
        status = 1; #状态码（0：新用户，1：用设备号注册，2：有手机号或者微信的用户）
        wid = ""; #微信ID
    }

###MagicPuller

**url:** http://HOSTNAME/BlingoServlet/MagicPuller?

**method:** GET

+---+---+----+
| p | t | de |
| a | y | sc |
| r | p |    |
| a | e |    |
| m |   |    |
| s |   |    |
+===+===+====+
| n | s | 用户 |
| n | t | 名（ |
|   | r | dd |
|   | i | /p |
|   | n | p/ |
|   | g | ww |
|   |   | ） |
+---+---+----+
| v | s | 客户 |
| v | t | 端版 |
|   | r | 本号 |
|   | i | （如 |
|   | n | 1. |
|   | g | 0表 |
|   |   | 示A |
|   |   | le |
|   |   | x系 |
|   |   | 列， |
|   |   | 1. |
|   |   | 1表 |
|   |   | 示蓝 |
|   |   | 天城 |
|   |   | 系列 |
|   |   | 等。 |
|   |   | 该参 |
|   |   | 数为 |
|   |   | 明码 |
|   |   | 。下 |
|   |   | 同。 |
|   |   | 如v |
|   |   | 2. |
|   |   | 0表 |
|   |   | 示小 |
|   |   | 雨系 |
|   |   | 列， |
|   |   | v2 |
|   |   | .1 |
|   |   | 表示 |
|   |   | ph |
|   |   | on |
|   |   | ic |
|   |   | s系 |
|   |   | 列， |
|   |   | v2 |
|   |   | .5 |
|   |   | 表示 |
|   |   | 长轴 |
|   |   | 小雨 |
|   |   | 系列 |
|   |   | ，v |
|   |   | 4. |
|   |   | 10 |
|   |   | /v |
|   |   | 4. |
|   |   | 11 |
|   |   | /v |
|   |   | 4. |
|   |   | 12 |
|   |   | /v |
|   |   | 4. |
|   |   | 13 |
|   |   | 表示 |
|   |   | 魔岛 |
|   |   | 系列 |
|   |   | ） |
+---+---+----+
| s | i | 精简 |
| s | n | 类型 |
|   | t | （0 |
|   |   | （默 |
|   |   | 认值 |
|   |   | ）： |
|   |   | 拉取 |
|   |   | 所有 |
|   |   | （第 |
|   |   | 一次 |
|   |   | 拉取 |
|   |   | ）； |
|   |   | 1： |
|   |   | 场景 |
|   |   | 状态 |
|   |   | 信息 |
|   |   | +系 |
|   |   | 列价 |
|   |   | 格信 |
|   |   | 息（ |
|   |   | 交易 |
|   |   | 后拉 |
|   |   | 取） |
|   |   | 2： |
|   |   | 场景 |
|   |   | 状态 |
|   |   | 信息 |
|   |   | （退 |
|   |   | 出场 |
|   |   | 景后 |
|   |   | 拉取 |
|   |   | ）） |
+---+---+----+
| t | i | 登录 |
| t | n | 方式 |
|   | t | (0 |
|   |   | （默 |
|   |   | 认） |
|   |   | ：设 |
|   |   | 备号 |
|   |   | ；1 |
|   |   | ：手 |
|   |   | 机号 |
|   |   | /微 |
|   |   | 信号 |
|   |   | )  |
+---+---+----+

**rtype:** json

**return:** 成功返回

::

    {
    scenes =     (
                {
            asset = 1; # 服务器端是否有下载资源
            cname = "\U5bb6\U5ead\U6210\U5458"; # 中文名称
            courses = "grandpa,grandma,father,mother,brother"; # 教学场景单词
            ename = "1. Learn-Families"; # 英文名
            intro = "grandpa,grandma,father,mother,brother"; # 关键词介绍
            lock = 1; # 是否锁住
            name = "course_family"; # 文件名
            paid = 1; # 是否付费
            pts = 0; # 得分
            state = 0; # 状态
            time = 0; # 所用时间
        },
                {
            asset = 1;
            cname = "\U5bb6\U5ead\U5168\U5bb6\U798f";
            ename = "1. Anna's Family";
            intro = "mother, father, grandma, grandpa, little brother, sister";
            lock = 1;
            name = "kid_mi_family";
            paid = 1;
            pts = 93;
            rounds = 5;
            state = 1;
            time = 186;
        },
                {
            asset = 1;
            cname = "\U52a8\U4f5c";
            courses = "jump,climb,run,eat,bark";
            ename = "2. Learn-Actions";
            intro = "jump,climb,run,eat,bark";
            lock = 1;
            name = "course_actionDog";
            paid = 1;
            pts = 0;
            state = 0;
            time = 0;
        },
                .
                .
                .
                
                {
            asset = 1;
            cname = "\U6709\U591a\U5c11\U4e2a\U6c14\U7403";
            ename = "7. How Many Balloons";
            intro = "one, two, three, four, five, six, seven";
            lock = 1;
            name = "kid_mi_number";
            paid = 1;
            pts = 0;
            rounds = 7;
            state = 0;
            time = 0;
        }
    );
    series =     (
                {
               {
            name = "magic_season12"; #系列名
            off = 0; # 是否打折
            price = 0; # 价格
        },
                {
            name = "magic_season13";
            off = 0;
            price = 3;
        }
    );
    }

###HelloHello

**url:** http://HOSTNAME/BlingoServlet/HelloHello?

**method:** GET

+--------+--------+------------------------------------+
| params | type   | desc                               |
+========+========+====================================+
| file   | string | 脚本名                             |
+--------+--------+------------------------------------+
| data   | string | 用户语音文本                       |
+--------+--------+------------------------------------+
| nn     | string | 用户设备名或登录名                 |
+--------+--------+------------------------------------+
| role   | string | 选择的机器角色代号(0 – 女, 1 – 男) |
+--------+--------+------------------------------------+
| rr     | string | 随机数                             |
+--------+--------+------------------------------------+

**rtype:** string

**return:** 成功返回

::

    . . . 今天我们来学习几种简单的颜色！:scripts/course_family/A0-K-B-0.ogg:A0:P1: 
    . . . Look!:scripts/courseModule/B0-K-B-0.ogg:B0:: 
    . . . This is grandpa, 爷爷. :scripts/courseModule/B4-K-B-0.ogg+scripts/course_family/grandpa_1.ogg+scripts/course_family/grandpa_ch.ogg:B4:P1-grandpa: 
    . . . 跟我读, grandpa.:scripts/courseModule/B1-K-B-0.ogg+scripts/course_family/grandpa_1.ogg:B1::
    # . . . 文本信息:音频:动画号:传给unity端颜色类型（p0，p1，p3时为需要飞入的球的颜色；p2时为选择题的正确答案；p4时为球需要变成的颜色）:
    # . . . 文本信息:音频:动画号::
    # . . . 文本信息:音频1+音频2+音频3:动画号:传给unity端颜色类型:
    # . . . 文本信息:音频1+音频2:动画号::

or

::

    . . . Yes, you are right!:scripts/kid_mi_family/3-0-P-K-B-0.ogg:5:10: 
    . . . Look, who is she? 再猜猜看她是谁？不知道怎么说也没关系，点一下右上角的灯泡寻求帮助吧！:scripts/kid_mi_family/3-1-K-B-0.ogg:6:-2:She is your grandma.
    # . . . 文本信息:音频:动画号:分数（-1 - 失败；-2 - 无用；>0 - 得分）:
    # . . . 文本信息:音频:动画号:分数:帮助内容

     

###MagicQuerier

**url:** http://HOSTNAME/BlingoServlet/MagicQuerier?

**method:** GET

+--------+--------+-------------+
| params | type   | desc        |
+========+========+=============+
| code   | string | (加密)VIP码 |
+--------+--------+-------------+

**rtype:** json

**return:** 成功返回

::

    {