| DTS2022101804917 | 【WeLink交付】【接口测试】更新app接口更新时需要带上所有的值，不带会重写一个默认值（/management/media-manage/v1/app/update） |
| ---------------- | ------------------------------------------------------------ |
| DTS2022100904626 | 结束跨站会议同步国外站点T_CM_CONFERENCE_ID表数据没有被清理。 |
| DTS2022092400512 | 【功能环境】【/40003-businessStatesChanged 更新会议业务状态】网络研讨会，调用更新会议业务状态接口报错500，日志打印空指针 |
| DTS2022092400354 | 【功能环境】【/10033-switchWaitingRoomState 打开/关闭等候室】公开会议主持人会中打开等候室，报错2000，Failed to switch wait room |
| DTS2022092303791 | 【功能环境】【AR000JF1SH 会议支持开会过程中修改会议信息】会议支持会中修改会议类型（P2P修改二转三会议），报错400，update.cloudConferenceUpdateReq.conferenceSettings.type: must be greater than or equal to 0 |
| DTS2022092600247 | 【功能环境】【AR000JF1SH 会议支持开会过程中修改会议信息】会中云云修改会议信息，未更新ownerNickname，报错400，invalid field ownerNickname |
| DTS2022092712764 | 【功能环境】【AR000JF1SH 会议支持开会过程中修改会议信息】会中云云修改会议信息，下发132的通知里participants列表为空 |
| DTS2022090615636 | 【功能环境】【AR000JF1SH 会议支持开会过程中修改会议信息】会议已开始，端云修改会议信息成功，收不到132通知 |
| DTS2022091907179 | 【功能环境】音乐加入直播间鉴权，报错401，check token error   |
| DTS2022061413718 | 登陆冲突 与 websocket 断连回调 无法确保前者先下发 需要优化登出逻辑 |
| DTS2022080308359 | 【LinkNow2.0.1.100mirror】【SIT】预约会议添加与会者预约成功后，被邀请与会者会议卡片和会议模块未同步会议数据 |
| DTS2022072703754 | 【网络研讨会】【主持人退会转移主持人给观众】【必现】新主持人没有切换角色，导致打开摄像头没有画面 |
| DTS2022070812613 | 003创建接入的业务，设置：startingInConferenceLimit为2,创建接入的业务，创建会议，与会者1加入会议1，与会者2加入会议,1，创建会议2，与会者2加入会议2，创建会议3，与会者3加入会议3，提示2009，用例单跑成功，批跑就会报400 |
| DTS2022080100636 | 【性能基线环境】加入会议报错500，not close json text, token : ,，请修改 |
| DTS2022080205995 | 【功能环境】加入直播间接口报错500，Invocation error；加入会议接口报错500，Internal Server Error，后台日志打印均报错500，请修改 |
| DTS2022072804697 | 功能环境，创建跨站会议，国外站点的T_CM_CONFERENCE_ID表为空，查询不到9位会议ID的数据 |
| DTS2022072300548 | 功能环境，创建会议接口批量报错500，Internal Server Error，日志打印空指针 |
| DTS2022072303107 | 跨租户会议，与会者不携带participantCode调queryByCode、query接口查询会议信息成功 |
| DTS2022072302604 | 功能环境，与会者提前入会，主持人加入会议后，提前入会的与会者收不到228事件 |
| DTS2022072302778 | 功能环境，指定appId配置支持9位会议接入号，与会者加入会议报错2060，join advance success!，请修改 |
| DTS2022062301381 | jni接口对齐 下载文件返回文件名                               |
| DTS2022062113274 | 功能对齐 sendClientRead 支持向自己发送                       |
| DTS2022061009363 | 【HWIMSDK】【跨站镜像】国外用户给国内用户发送离线消息，发送完成后国外用户离线，国内用户上线接收消息，存在消息丢失 |
| DTS2022051113782 | 【N】【自动化】【国内灰度】【多端登录】AB手机同时登录同一个华为帐号进行互踢操作，A手机点击重新上线按钮后，B手机概率性出现登录冲突的提示，不是被踢的提示，请开发定位并修改 |
| DTS2022053114185 | 【必现】【跨站灰度】【智能关怀】亚非拉用户A给中国用户B发送图片消息，富文本加解密失败 |
| DTS2022052002559 | 【偶现】【国内开发】智能关怀 发送端侧已读 返回 1 sdk 内部重试 消息发送成功 无法理解 错误码 1 |
| DTS2022060103558 | 【HWIMSDK】【跨站镜像】国内给欧洲发送在线消息，存在消息丢失  |
| DTS2022052014036 | 打点上报 crashinfo、KiExeception可能泄露用户数据 需要和keyindex 确认，排查整改 |
| DTS2022052013607 | Log error级别打印了Exception错误信息                         |
| DTS2022051204003 | 【CVE-2022-24823】Netty is an open-source, asynchronous event-driven network application framework. The package `io.netty:netty-codec-http` prior to version 4.1.77.Final contains an insufficient fix for CVE-2021-21290. When Netty's multipart decoders are us |
| DTS2022050909491 | ImSdk Cpp Android Demo 优化 适配文件多进度回调               |
| DTS2022050707953 | 【CVE-2022-25647】The package com.google.code.gson:gson before 2.8.9 are vulnerable to Deserialization of Untrusted Data via the writeReplace() method in internal classes, which may lead to DoS attacks. |
| DTS2022050905531 | Json 2.8.6 存在漏洞 需要升级版本 2.9.0                       |
| DTS2022050711744 | security 1.1.5.306 存在安全漏洞 需要升级 1.1.5.310           |
| DTS2022042601211 | 登陆失败 后sdk 内部会重试三次 三次任然没有连接成功会再 刷新 trs 再尝试重连 WssInfo刷新依赖网络请求 失败时返回 null 此时调用 wssinfo 内部方法就会报控制针异常 需要避免被刷新为空 并做空判断 |
| DTS2022042006656 | 【现网】【偶现】LinkNow 网络波动 无法发送消息 重开应用可以恢复 |
| DTS2022031013317 | 【IM SDK】【Social】【偶现】版本号Social 650，测试环境，登录正常，websocket是断开的，消息一直loading（超时） |
| DTS2022031612746 | 【优化】发送消息只校验参数合法性 不合法参数不应该为业务补全默认缺省值 |
| DTS2022030814565 | grs 版本升级                                                 |
| DTS2022021614714 | 【HWIMSDK】【镜像跨站】中国用户A，欧洲用户B，B给A发送几条跨站聊天，A卸载linknow再重新登录，会话列表拉取最新一条消息，通知栏显示"正在等待消息" |
| DTS2022021016210 | danmu sdk 优化 demo 支持编辑 appid roomid 弹幕内容 等级      |
| DTS2022021707641 | 【N】【欧洲灰度环境】欧洲用户A退出登录，然后国内用户B给欧洲用户发送消息，国内用户B再建一个包含A的普通跨站群，B再在群里发消息，A再登录，A只收到了单聊消息而没收到群聊消息 |
| DTS2022030313863 | 【偶现】【国内镜像】连续断网重连后，消息发送失败             |
| DTS2022021609223 | 【N】【镜像环境】【跨站】欧洲用户给中国用户互发消息，接收方接收很慢 |
| DTS2022030409329 | 【IM】 Hms core 6.4.0.303，测试环境，连接显示正常，消息发送超时，接收不到消息 |
| DTS2022021813792 | 【N】【灰度环境】【单聊】发送消息一直失败                    |
| DTS2022012611949 | 【HWIMSDK】【跨站聊天】国内A给欧洲用户B发送语音通话，发起方在发起语音十几秒后，接收方才出现语音接听界面，点击接听，提示对方已取消，但发起方仍在通话中。再次发起语音通话，国内A直接提示通话中断、已取消或其他多媒体会话进行中，等待十几秒之后，接收方B连续出现语音接收界面，并自动取消通话 |
| DTS2022011805790 | 【N】【欧洲现网】团队群中，群成员A删除并退出群后，其他群成员和群主的群内没有A退出时的提示语 |
| DTS2022012410157 | 【N】【镜像环境】欧洲用户被国内用户拉黑后，欧洲用户给国内用户发消息一直转圈，不是被拉黑后发消息的预期结果 |
| DTS2022020810658 | 【N】【灰度环境】点击消息首页进入对话框无反应                |
| DTS2022013000575 | 【偶现】【功能】P2P频繁快速呼叫挂断，SDK返回15003的错误码    |
| DTS2022020903409 | 【HWIMSDK】【欧洲镜像环境】发送富文本消息失败                |
| DTS2022021003616 | 视频开发 需要调试开发环境 添加变体 支持danmu-mirror.hwcloudtest.cn |
| DTS2022012203758 | 日志不够友好，release包会混淆一些信息，打印不够全面，详细。  |
| DTS2022012510453 | [国内镜像] 发送消息成功的ACK 服务器没有返回这个msg 的seq 业务层[撤回消息]需要这个字段 |
| DTS2022012200318 | 以前版本屏蔽了tcp 发送弹幕 为了测试服务器状态 建议内部实现 由外部决定是否禁用 tcp |
| DTS2021122807468 | 【功能】【linknow】【全场摄像头/全场麦克风优化】【必现】主持人邀请与会者打开摄像头/麦克风，与会者弹框提示《主持人申请打开您的麦克风/摄像头》，未对弹框做定时，应超过2分钟弹框自动销毁 |
| DTS2021122114656 | 【MediaSdk 1.1.0】使用int型来接收服务器的Integer数据，若服务器字段为null时，会导致客户端Crash |
| DTS2021121708497 | 【CVE-2021-43797】Netty is an asynchronous event-driven network application framework for rapid development of maintainable high performance protocol servers & clients. Netty prior to version 4.1.7.1.Final skips control chars when they are present at the be |
| DTS2021122806883 | 【视频会议】【现网环境】【MediaSdkIOS 1.0.1.300】【必现】主持人邀请与会者打开摄像头/麦克风，与会者端弹框未在两分钟后消失 |
| DTS2021102115603 | 【linknow1.1.0.100】【折叠屏】【会议】会前页面在折叠屏的展开形态应支持横竖旋转；会议直播间更多按钮展开内容不应因屏幕形态切换消失。 |
| DTS2021120819559 | 【N】【国内镜像】【离线信息收到】三方手机收不到离线消息      |
| DTS2021102112604 | 【CVE-2021-37137】The Snappy frame decoder function doesn't restrict the chunk length which may lead to excessive memory usage. Beside this it also may buffer reserved skippable chunks until the whole chunk was received which may lead to excessive memory us |
| DTS2021102510468 | 【CVE-2021-37137】The Snappy frame decoder function doesn't restrict the chunk length which may lead to excessive memory usage. Beside this it also may buffer reserved skippable chunks until the whole chunk was received which may lead to excessive memory us |
| DTS2021092920599 | [Link Now PC v1.0.9.300] - Participants are not notified when host has extended the scheduled meeting duration during ongoing meeting. |
| DTS2021110211078 | 【功能】【linknow版本1.1.0】【LT语言翻译问题功能确认】【必现】【全球化HMOS2.1LT10语言测试“功能问题”确认】翻译专家反馈 有部分页面词条显示、用法或者翻译不对，请修改 |
| DTS2021102215636 | 【视频会议】【镜像环境】【MediaSdk 1.0.9.300】【必先】与会者页面搜索与会者，然后点击与会者，弹框背景色与搜索页的背景颜色一致 |
| DTS2021092618765 | 【MediaSdk 1.0.8】更新MediaSdk 1.0.8接口变更至接口文档       |
| DTS2021102115435 | 【LinkNow】【Conference】【1.0.9.300】【代码规范整改】【删除所有对MediaDataWrapper.getInstance().XXX的调用】 |
| DTS2021093012793 | 【功能】【linknow版本1.1.0】【美颜预览】【crash】【必现】会中关闭美颜，退出会议后，再从我的-设置 打开美颜，进行美颜预览会crash |
| DTS2021101912620 | 【功能】【linknow版本1.1.0】【手放下】【必现】与会者举手后，主持人使用搜索功能搜索该与会者，在搜索后的页面无法点击举手图标把 与会者手放下，请修改 |
| DTS2021101417356 | 【功能】【linknow版本1.1.0】【屏幕共享】【必现】与会者首次开启屏幕共享时会返回到系统桌面，此时主持人结束与会者屏幕共享，与会者没有跳转到应用内，还显停留在手机桌面 |
| DTS2021101927033 | 【会议】【MeidaSdk 1.0.9.111】【Conference 1.0.9.108】 用户进入会议后直接进入驾驶模式 ClassCastException |
| DTS2021093012309 | 【MediaSdk 1.0.9】MediaSdk所有对外接口，入参设计会议ID、会议Code的，需要加入防护 |
| DTS2021090621660 | 【功能】【linknow版本1.1.0】【UX】【必现】当有音视频使用，右上角“+” 发起快捷会议，这个弹框文字需要居中对齐，请修改 |
| DTS2021092812081 | 【MediaSdk 1.0.9】共享时在应用内不能标注 停止共享不能返回会中 |
| DTS2021090212154 | 【linknow版本1.0.9】【monkey测试】java.lang.RuntimeException: Unable to destroy activity {com.huawei.welinknow/com.huawei.cloudservice.appgallery.linknow.business.conference.ui.LinkJoinConfActivity}: java. |
| DTS2021090114069 | 【MediaSdk 1.0.8.300】【MediaSdk 1.0.9.300】未开启上层显示权限的情况下，部分Dialog无法弹出，可能导致功能异常 |
| DTS2021090711075 | 【MediaSdk 1.0.8.300】MediaSdk内部的默认通知推送类，不应使用固定的ChannelId，应使用HwShareConfig中的ChannelId |
| DTS2021090120411 | 【MediaSdk 1.0.8.300/1.0.9.300】优化ShareConfig参数传递流程，与Link Now业务解绑 |
| DTS2021083020211 | 【MediaSdk 1.0.8.300】混淆后，关键日志无法识别当前类，需要重写TAG获取的逻辑 |
| DTS2021083020972 | 【功能】【linknow版本1.0.9】【会中】【必现】本地视频分辨率，二选一切换 建议修改成 选择后自动返回上一界面 |
| DTS2021083011627 | 【MediaSdk 1.0.8.300】MediaSdk内部的默认通知推送类，不应使用固定的ChannelId，应使用HwShareConfig中的ChannelId |
| DTS2021082625233 | 【功能】【linknow版本1.0.9】【会前】【UX】【必现】网络波动断开,弹出对话框,当网络恢复正常后,可以优化修改成 弹框自动销毁, |
| DTS2021082328243 | 【功能】【linknow版本1.0.9】【摄像头和麦克风权限】【必现】会前预览，如果关闭了摄像头和麦克风权限 ，发起会议 或者 加入会议 预览的摄像头和麦克风因为没有使用，进入会议前 就不需要再次弹出对话框了，建议修改 |