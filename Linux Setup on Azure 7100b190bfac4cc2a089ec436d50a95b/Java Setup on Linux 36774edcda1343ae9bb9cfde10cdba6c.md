# Java Setup on Linux

Download and install JDK 17 (latest version as of Jan 2022)

```bash
wget https://download.oracle.com/java/17/latest/jdk-17_linux-x64_bin.deb
sudo apt install ./jdk-17_linux-x64_bin.deb
```

Reference:  [https://www.how2shout.com/linux/oracle-java-ubuntu-22-04/](https://www.how2shout.com/linux/oracle-java-ubuntu-22-04/)

Configure.

```bash
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk-17/bin/java" 1
sudo update-alternatives --set java /usr/lib/jvm/jdk-17/bin/java
```

Verify the installation. Should print the installed and configured version.

```bash
java --version

java 17.0.1 2021-10-19 LTS
Java(TM) SE Runtime Environment (build 17.0.1+12-LTS-39)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.1+12-LTS-39, mixed mode, sharing)
```

To uninstall: sudo apt purge jdk-17