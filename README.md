# Customized LXC templates for Proxmox

為了避免每次建立新的 Container 都要重複設定，所以客製化 template 來使用

基本上是參考這個專案：https://github.com/frieder/dab-templates

## 環境

使用 Proxmox 建立一台 Proxmox VM，然後安裝 dab
```
apt update && apt install dab
```

## Create template
```
cd ubuntu-20.04
make
```
## Add template
```
mv xxx.tar.gz /var/lib/vz/template/cache/
```
