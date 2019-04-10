`V2Ray`環境構築手順

# 1. VM作成
　お薦めサイト
- [Google Cloud Platform](https://cloud.google.com/free/?hl=ja)　※1年間の無料トライアルあり

- [Bandwagon Host](https://bwh88.net/clientarea.php)　※CN2線路は中国電信に優しい

- [Microsoft Azure](https://azure.microsoft.com)　※スピードは速くないため、候補として使う

　上記で作成したサーバーIPをまず[IPIP](https://tools.ipip.net/ping.php)で`ping`結果を確認し、遅いなら地域を変更して作り直す。

# 2. SS(R) #

## 2.1 Server構築方法
- SSHでサーバーへ接続する

  OS：`Debian9`、`Centos7.5` 限定。

- root権限取得

  `sodu -i`
  
- wgetをインストール

 `yum -y install wget`
 
- SS(R)をインストール

 `wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh`
 
- BBR加速
  
  `rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org`
  
  `rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-3.el7.elrepo.noarch.rpm`
  
  `yum --enablerepo=elrepo-kernel install kernel-ml -y`
  
  `egrep ^menuentry /etc/grub2.cfg | cut -f 2 -d \'`
  
  `grub2-set-default 0  # default 0` 表示第一个内核设置为默认运行, 选择最新内核就对了
  
 - 再起動
 
  `reboot`

  `modprobe tcp_bbr`
  
  `echo "tcp_bbr" >> /etc/modules-load.d/modules.conf`
  
  `echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf`
  
  `echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/s ysctl.conf`
  
  `sysctl -p`
  
  -下記実行結果に`bbr`のあることを確認
 
  `sysctl net.ipv4.tcp_available_congestion_control`
  
  -下記実行結果に`bbr`のあることを確認
  
  `sysctl net.ipv4.tcp_congestion_control`
  
  -下記実行結果に`tcp_bbr`のこあることを確認
  
  `lsmod | grep bbr`
  
  
- 接続情報を保存

# 3. V2ray
- 技術関連は[Homepage](https://www.v2ray.com/)を確認

## 3.1 Server構築方法
- SSHでサーバーへ接続する

  OS：`Debian9`、`Centos7.5` 限定。

- root権限取得

  `sodu -i`

- V2rayをインストール

  `bash <(curl -s -L https://git.io/v2ray.sh)`　←たった1行のコマンドでBBRまで設定してくれる

　 基本は全部デフォルト値でEnterキー連発

　   　Domainを持っている方は`Websocket＋TLS`がお勧め。Domain申請:[Freenom](https://www.freenom.com)


- 接続情報を保存


## 3.2 V2ray Client ##
### 3.2.1 Windows ###
`V2rayN`

https://github.com/2dust/v2rayN/releases

### 3.2.2 Mac ###
`V2rayX`

https://github.com/Cenmrev/V2RayX/releases

### 3.2.3 iOS ###
`ShadowRocket`

海外AppleStoreからダウンロード（有料）。
>Support:SS、SSR、V2ray...お薦め

### 3.2.4 ASUS Router ###
`Koolshare`官改 GT-AC5300例

- 官改固件

  http://koolshare.cn/thread-130902-1-1.html
 からダウンロード

- `shadowsocks.tar.gz` 不可描述Plugin（offline Install）

  https://github.com/hq450/fancyss


### 3.2.5 Android ###
中国製設備ならまずはRootから～

`V2rayNG`

https://github.com/2dust/v2rayNG/releases



