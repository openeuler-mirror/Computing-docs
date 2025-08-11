# Installation and Deployment

## Software and Hardware Requirements

- Hardware: Kunpeng 920 server

- Software: openEuler 23.09

## Environment Preparation

- Install the openEuler OS.

- Obtain root permissions.

## sysBoost Installation

To install the sysBoost, perform the following steps (**xxx** in the commands indicate version numbers):

1. Mount an openEuler ISO image.

    ```sh
    # Use the ISO file of the corresponding openEuler version.
    mount openEuler-xxx-aarch64-dvd.iso /mnt
    ```

2. Configure a local Yum source.

    ```sh
    vim /etc/yum.repos.d/local.repo
    ```

    The configured contents are as follows:

    ```text
    [localosrepo]
    name=localosrepo
    baseurl=file:///mnt
    enabled=1
    gpgcheck=1
    gpgkey=file:///mnt/RPM-GPG-KEY-openEuler
    ```

3. Install sysBoost.

    ```sh
    yum install sysboost -y
    ```

4. Check whether the installation is successful.

    ```text
    # rpm -qa | grep sysboost
    sysboost-xxx
    # rpm -qa | grep native-turbo
    native-turbo-xxx
    ```

    If the preceding information is displayed, the installation is successful.

5. Install the relocation packages required for combining the ELF files.

    ```sh
    yum install bash-relocation-xxx -y 
    yum install ncurses-relocation-xxx -y
    ```

    > ![](./figures/icon-note.gif) **Note:**  
    > If the ELF files and their dependency libraries contain the relocation segment, skip this step.
