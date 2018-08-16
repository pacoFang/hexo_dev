网络代理服务器的安装与使用

1.下载
地址:git@github.com:abhinavsingh/proxy.py.git
2.打开下载目录
pip install proxy.py
3.启动服务,指定host和端口
proxy.py --hostname 0.0.0.0 --port 1111

注意:host要用0.0.0.0

4.设置代理
以firefox为例,打开设置页面,->网络代理->选择手动代理->输入ip和端口即可