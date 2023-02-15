Quantumult X
关于换区

解锁并换区：将CN改为想看的国家/地区的2位大写英文简写，

在HTTP复写中，将CN的替换值改为SG、MO、TW等即可换区
操作步骤

1、打开Quantumult X

2、开启MitM并信任Quantumult X证书： * 设置 → MitM → 开启MitM → 生成密钥及证书 → 右上角点保存 → 允许安装描述文件 → 关闭 → 前往手机的设置，不在Quantumult X了 → 看到已下载描述文件 → 安装 → 输入手机的解锁密码 → 安装 → 安装 → 前往手机的设置 → 通用 → 关于本机 → 证书信任设置 → 找到Quantumult X Custom Root Certificate…点绿它以信任该根证书 → 继续

方法一：

3、配置文件点击编辑找到[rewrite_remote]添加下面对应国家的复写

日本

https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Quantumult-X/TikTok-JP.conf, tag=TikTok, update-interval=86400, opt-parser=false, enabled=true
台湾

https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Quantumult-X/TikTok-TW.conf, tag=TikTok, update-interval=86400, opt-parser=false, enabled=true
韩国

https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Quantumult-X/TikTok-KR.conf, tag=TikTok, update-interval=86400, opt-parser=false, enabled=true
美国

https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Quantumult-X/TikTok-US.conf, tag=TikTok, update-interval=86400, opt-parser=false, enabled=true
方法二：

3、在[rewrite_local]中添加以下重写

(?<=_region=)CN(?=&) url 307 KR
(?<=&mcc_mnc=)4 url 307 2
^(https?:\/\/(tnc|dm)[\w-]+\.\w+\.com\/.+)(\?)(.+) url 302  $1$3
(?<=\d\/\?\w{7}_\w{4}=)1[6-9]..(?=.?.?&) url 307 17
3.1、在[mitm]中添加

hostname = *.tiktokv.com, *.byteoversea.com, *.tik-tokapi.com
4、找到[filter_remote]添加下句分流(无论使用方法一或是方法二，此分流都需要添加！)

https://raw.githubusercontent.com/Semporia/TikTok-Unlock/master/Quantumult-X/TikTok.list, tag=TikTok, force-policy=TikTok, update-interval=86400, opt-parser=false, enabled=true
5、换区：在[rewrite_local]中添加下句重写，并将CN改为想看的国家/地区的2位大写英文简写 JP（日本）｜KR（韩国）｜UK（英国）｜US（美国）｜TW（台湾）

(?<=_region=)CN(?=&) url 307 CN
6、开启Quantumult X：前往Quantumult X的主页 → 找到TikTok策略 → 长按添加节点 → TikTok愉快

