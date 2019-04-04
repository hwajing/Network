# 1. VM作成
　お薦めサイト
- [Google Cloud Platform](https://cloud.google.com/free/?hl=ja)　※1年間の無料トライアルあり

- [Bandwagon Host](https://bwh88.net/clientarea.php)　※CN2線路は中国電信に優しい

- [Microsoft Azure](https://azure.microsoft.com)　※第3後備

　上記で作成したサーバーIPをまず[IPIP](https://tools.ipip.net/ping.php)で`ping`結果を確認

# 2. V2ray Server
[V2ray Homepage](https://www.v2ray.com/)

## 2.1 構築方法
- SSHでサーバーへ接続する

  OS：`Debian9`　か　`Centos7.5` 限定

- root権限取得

  `sodu -i`

- V2rayをインストール

  `bash <(curl -s -L https://git.io/v2ray.sh)`

　基本は全部デフォルト値でEnterキー連発

　Domainを持っている方は`Websocket＋TLS`がお勧め
 
 - Domain申請:[Freenom](https://www.freenom.com)


- 接続情報を保存


# 3. V2ray Client #
## 3.1 Windows ##
`V2rayN`

https://github.com/2dust/v2rayN/releases

## 3.2 Mac ##
`V2rayX`

https://github.com/Cenmrev/V2RayX/releases

## 3.3 iOS ##
`ShadowRocket`

海外AppleStoreからダウンロード（有料）。
>Support:SS、SSR、V2ray...お薦め

## 3.4 ASUS Router ##
`Koolshare`官改 GT-AC5300例

- 官改固件

  http://koolshare.cn/thread-130902-1-1.html
  からダウンロード

- `shadowsocks.tar.gz` 不可描述Plugin（offline Install）

  https://github.com/hq450/fancyss


## 3.5 Android ##




