# hugo

## 安装(wsl)
```sh
#!/bin/bash
cd /tmp

# 要换版本，直接改下面这行的数字就行
VERSION="0.159.0" 

wget https://github.com/gohugoio/hugo/releases/download/v${VERSION}/hugo_extended_${VERSION}_linux-64bit.tar.gz

tar -xzf hugo_extended*.tar.gz hugo
sudo mv hugo /usr/local/bin/

hugo version
```