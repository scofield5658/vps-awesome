## 基本步驟

1. 登錄

```bash
ssh your_name@your_ip -p your_port
```

2. 安裝必備依賴庫

```bash
sudo apt-get install wget vim golang
sudo apt-get install build-essential libssl-dev
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
```

3. 創建文件夾

```bash
mkdir Logs
mkdir Codes
mkdir Downloads
```

4. 設置環境變量

```bash
export GOPATH="$HOME/Codes/GoLib"
export PATH=$PATH:${GOPATH//://bin:}/bin
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
```

5. 安裝相關工具

```bash
# Optional
nvm install node
npm install -g yarn

# Essential
go get github.com/shadowsocks/shadowsocks-go/cmd/shadowsocks-server
```

6. 啟動腳本與執行權限

```bash
#!/bin/sh
nohup shadowsocks-server -c $(dirname $0)/config.json > $HOME/Logs/SS.log 2>&1 &
```

```bash
sudo chmod 755 start.sh
```


7. 修改防火墻規則

```bash
sudo ufw allow 15658
```
