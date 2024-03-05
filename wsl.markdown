# wsl使用记录

## 导入导出wsl

1. 查看已经安装的系统

    ``` cmd
    wsl --list 
    ```

2. 导出系统到指定位置

    ``` cmd
    wsl --export Ubuntu D:\Ubuntu.tar
    ```

3. 删除当前系统, 也可以不删除

   ```cmd
    wsl --unregister Ubuntu
   ```

4. 导入系统到指定位置

    ```cmd
    wsl --import Ubuntu D:\Ubuntu D:\Ubuntu.tar --version 2
    ```

5. 设置默认用户

    ```cmd
    ubuntu config --default-user xxxx
    
    ```

## 开启普通用户端口权限

打开/etc/sysctl.conf

``` text
net.ipv4.ip_unprivileged_port_start = 53 //端口起始位置
```

在命令行输入 ``` sysctl -p ``` 执行修改

## 添加dns

打开/etc/resolv.conf，添加以下代码

```text
nameserver xxx.xxx.xxx.xxx  //dns的ip地址
```

## wsl开启systemd

打开/etc/wsl.conf，如果wsl.conf不存在需要手动创建wsl.conf
在wsl.conf添加以下代码

```text
[boot]
systemd=true
```

重启wsl
输入 ``` ps --no-headers -o comm 1 ``` 看看是否显示systemd，显示systemd则开启成功
