# [ShadowTLS v3](https://github.com/ihciah/shadow-tls/tree/master)
- **Install dependencies**
```
apt update && apt -y install wget libc6-dev build-essential zlib1g-dev libssl-dev libevent-dev mingw-w64
```
- **Install go**
```
wget -c https://go.dev/dl/go1.20.5.linux-amd64.tar.gz -O - | tar -xz -C /usr/local && echo 'export PATH=$PATH:/usr/local/go/bin' > /etc/profile && source /etc/profile && go version 
```
- **Install sing-box**
```
go install -v -tags with_dhcp with_wireguard with_shadowsocksr with_ech with_utls with_gvisor with_clash_api with_lwip github.com/sagernet/sing-box/cmd/sing-box@latest && mv ~/go/bin/sing-box /usr/local/bin/
```
- **Download sing-box.service and config.json**
```
wget -P /etc/systemd/system https://raw.githubusercontent.com/TinrLin/ShadowTLS-v3-build-tutorial/main/sing-box.service && mkdir /usr/local/etc/sing-box && wget -P /usr/local/etc/sing-box https://raw.githubusercontent.com/TinrLin/ShadowTLS-v3-build-tutorial/main/config.json
```
- **Test if it works**
```
/usr/local/bin/sing-box run -c /usr/local/etc/sing-box/config.json
```
- **Check the current status**
```
systemctl daemon-reload && systemctl enable --now sing-box && systemctl status sing-box
