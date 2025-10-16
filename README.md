此项目为 [Home Assistant](https://www.home-assistant.io/) 的[巴法云](https://cloud.bemfa.com/)插件。
## 修复
修复高版本HA的mqtt版本不兼容导致的bemfa插件失效问题 25/09/10
修复参考（https://bbs.hassbian.com/thread-29794-1-1.html）帖子和评论
##如果你感觉本文对你有帮助，请关注公众号
![hacs_badge](扫码_搜索联合传播样式-标准色版.png)


## 功能
将 Home Assistant 实体同步至巴法云，并使用小爱同学/天猫精灵/小度音箱控制。

[![hacs_badge](https://img.shields.io/badge/HACS-Default-41BDF5.svg?style=for-the-badge)](https://github.com/hacs/integration)

## 使用
  1. 注册巴法云账号，并获取密钥
  2. 在HACS中搜索 bemfa 安装，或者 clone 此项目, 将 custom\_components/bemfa 目录拷贝至 Home Assistant 配置目录的 custom\_components 目录下。
  3. 重启 Home Assistant 服务。
  4. 在 Home Assistant 的集成页面，搜索 "bemfa" 并添加。
  5. 根据提示输入巴法云密钥后提交
  6. 安装成功后，点击集成左下角“选项”，同步需要的实体至巴法云。
  7. 在智能音箱App中添加巴法云设备:
     * 小爱同学: 在米家app-->我的-->其他平台设备-->点击添加-->找到"巴法"，输入巴法云账号即可，设备会自动同步到米家。
     * 天猫精灵: 打开天猫精灵app，在app中搜索：巴法云。找到巴法云技能，点击绑定账号，登陆你的巴法云账号.
     * 小度音箱: 打开小度音箱app或者小度app，在app首页点+号-->添加设备-->搜索巴法，找到"巴法"，输入巴法云账号即可。

## 优势
  1. 操作简单，只需要下载一个插件，且是可视化配置。
  2. 无需公网 ip, 无需 NR.

## 原理
巴法云使用 MQTT 与终端设备通信，每个设备对应一个主题。

此插件根据用户选择的需要同步的实体，调用巴法云 API 创建对应主题，将此实体的实时状态发布至此主题，并订阅此主题的信息以控制它。

## Q/A
  - Q: 哪些实体支持同步至巴法云？

    A: 受巴法云的限制，目前仅支持开关类，灯类，风扇类，窗帘类，空调类和温度/湿度/开关/光照传感器，并且对每种语音助手的支持各有稍许区别，例如小度音箱不支持风扇的摇头控制，具体参考[巴法云文档](https://cloud.bemfa.com/docs/#/)。此外，此插件将扫地机/脚本/自动化/场景/二元选择器/分组/摄像机/加湿器/媒体播放器/锁/遥控器/汽笛虚拟成开关类设备，可通过语音开关。

  - Q: 为什么调节灯的颜色时却是调的色温？

    A: 巴法云中灯的颜色和色温为同一个字段，此插件中无法精确区分。如果你的灯既可以调节颜色又可以调节色温，可能会出现混乱的情况。

  - Q: Home Assistant 中米家的设备本就支持小爱同学配置，还需同步至巴法云么？

    A: 不需要，并且不建议同步, 没必要经过巴法云绕一圈。

  - Q: 同时有小爱同学和天猫精灵，如何只同步非米家设备至小爱同学，并同步所有设备至天猫精灵？

    A: 目前没有太好的方案，一个可行的方案是注册2个巴法云账号，分别配置不同的插件实体进行同步，然后将2个账号分别绑定到小爱同学和天猫精灵。

## 捐赠
如果此项目对你有帮助，可以扫描下方二维码请我喝杯咖啡 :)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="donate/wechat.png" width="200" title="使用微信扫一扫" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src="donate/alipay.png" width="200" title="使用支付宝扫一扫" />
