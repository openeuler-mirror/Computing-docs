# 安装与部署

## 软硬件要求

- 硬件：鲲鹏920处理器

- 软件：操作系统openEuler 23.09

## 环境准备

- 安装openEuler系统。

- 安装sysBoost需要使用root权限。

## 安装sysBoost

安装sysBoost的操作步骤如下（xxx在以下描述中代表版本号）：

1. 挂载openEuler的iso文件

    ```sh
    # 使用对应的openEuler版本
    mount openEuler-xxx-aarch64-dvd.iso /mnt
    ```

2. 配置本地yum源

    ```sh
    vim /etc/yum.repos.d/local.repo
    ```

    配置内容如下所示：

    ```sh
    [localosrepo]
    name=localosrepo
    baseurl=file:///mnt
    enabled=1
    gpgcheck=1
    gpgkey=file:///mnt/RPM-GPG-KEY-openEuler
    ```

3. 安装sysBoost

    ```sh
    yum install sysboost -y
    ```

4. 验证是否安装成功，命令和回显如下表示安装成功

    ```sh
    rpm -qa | grep sysboost
    # sysboost-xxx
    rpm -qa | grep native-turbo
    # native-turbo-xxx
    ```

5. 安装需要合并的ELF文件所对应的relocation包

    ```sh
    yum install bash-relocation-xxx -y 
    yum install ncurses-relocation-xxx -y
    ```

> [!NOTE]说明
> 若当前所需要的可执行ELF文件及其依赖库中已经包含relocation段，则可以跳过步骤5。
