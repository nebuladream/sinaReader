
使用说明:

如果您使用demo出现问题时，请注意以下内容:

一 编译错误或者警告可能的问题
1、检查下有没有将iflyMSC.framework加入到本工程中。

2、检查下指令集是否设置正确。共有两个framework，分别对应armv6,armv7和armv7,armv7s

3、是否引入了sdk依赖的系统库AudioToolbox.framework、CFNetwork.framework、CoreGraphics.framework、QuartzCore.framework、SystemConfiguration.framework。


二 SDK运行中锁屏崩溃

运行SDK时，推荐使用Background模式，请在程序的plist文件见中加入以下内容

    <key>UIBackgroundModes</key>
    <array>
        <string>audio</string>
    </array>

如果您的程序运行在非Background模式，请在启动SDK前注册锁屏回调，并在回调中加入 cancel，也意味着锁屏时需要停止语音服务。

三 getUpflow和getDownflow方法运行崩溃
   1018之后的版本，增加了BOOL isTotal，TRUE表示某一项服务所有会话的流量，FALSE表示单词会话的流量，请注意指定参数值