# Linux Setup on Azure

This is how it looks after the setup.

![Untitled](Linux%20Setup%20on%20Azure%207100b190bfac4cc2a089ec436d50a95b/Untitled.png)

It is a Linux dev VM on Azure - the picture shows:

- a terminal running Confluent Kafka platform on Docker.
- VS code with a Java Spring Boot project.
- Confluent Control Centre opened in Firefox.
- System Monitor showing resource utilisation.

The dev VM currently has the following installed.

- Java 17
- .NET 6.0
- Rust
- Go
- VS code
- Docker
- Kafka

> Why this setup?
> 

The equivalent setup to do some concept work on Kafka using Java Spring Boot required a Azure VM double the size of Linux. 

The Azure setup required a VM of 8 CPUs and 32 GB memory to run the whole dev setup smoothly. The selected Azure VM was:

<aside>
🖥️ Standard D8s v3 (8 vcpus, 32 GiB memory). Running cost £232 per month.
Price valid as on Jan 2022.

</aside>

I could achieve the similar performance by using Linux with half the capacity of the Windows VM counterpart. Note: this is only for running a dev setup and not considering any of the performance requirements to run production workloads.

Sections below describes the Linux VM selection and dev setup.

> Azure Image
> 

Selected Ubuntu Linux distro.

| Distro | Ubuntu Server 21.10 - Gen1 |
| --- | --- |
| By | Canonical |
| Azure VM Size | Standard D4s v5 (4 vcpus, 16 GiB memory) |
| Cost | £116 per month. Price valid as on Jan 2022. |
| Enabled public inbound ports | SSH, RDP |
| OS disk type | Standard SSD LRS |

It is a server image which means there is no desktop capabilities installed (no GUI/RDP) to use it as a remote desktop. The VM running cost is half that of Windows as Windows 11 needed a much higher resources to run the same work load.

> Linux configuration
> 

To enable desktop based environment install a desktop environment.

Via Azure shell, install XRDP and Ubuntu Gnome desktop depending on SSH key or user id, password which was selected at the time of VM setup. 

The below steps shows SSH using user id and password.

```bash
SSH user@public-ip-address
```

🔶 Install GNOME desktop.

First command updates all packages followed by Ubuntu GNOME desktop environment installation.

```bash
sudo apt-get update
sudo apt install tasksel
sudo tasksel install ubuntu-desktop
```

Reference: [https://linuxconfig.org/how-to-install-gnome-on-ubuntu-20-04-lts-focal-fossa](https://linuxconfig.org/how-to-install-gnome-on-ubuntu-20-04-lts-focal-fossa)

🔶 Install XRDP.

```bash
sudo apt-get -y install xrdp
sudo systemctl enable xrdp
```

Reference:  [https://docs.microsoft.com/en-us/azure/virtual-machines/linux/use-remote-desktop](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/use-remote-desktop)

After these steps, restart VM and login via remote desktop tool of your choice. I’ve tested with Microsoft Remote Desktop on mac.

Who doesn’t like dark mode and bit of tweaking? Let’s do that now.

To enable dark mode, install GNOME extensions.

```bash
sudo apt install gnome-shell-extensions
sudo apt install gnome-tweaks
```

Reference: 

- [https://vitux.com/how-to-enable-dark-mode-in-ubuntu-20-04-lts/](https://vitux.com/how-to-enable-dark-mode-in-ubuntu-20-04-lts/)
- [https://askubuntu.com/questions/1213047/how-to-quickly-switch-to-dark-mode-in-ubuntu-with-gnome-and-to-make-it-fully-d](https://askubuntu.com/questions/1213047/how-to-quickly-switch-to-dark-mode-in-ubuntu-with-gnome-and-to-make-it-fully-d)

Optional but I’d prefer the snap store installation for discovering installing Debian packaged apps.

Install snap store.

```bash
sudo apt update
sudo apt install snapd
sudo snap install snap-store
```

Reference: [https://snapcraft.io/install/snap-store/ubuntu](https://snapcraft.io/install/snap-store/ubuntu)

If you have reached till here then it means the linux dev VM is successfully setup and you are able to do a remote login to the linux desktop environment. The linux could have been used via SSH instead of the desktop environment but that is for another day and another note.

⚙️ Next up: install and configure the languages and frameworks required for development.

[Java Setup on Linux](Linux%20Setup%20on%20Azure%207100b190bfac4cc2a089ec436d50a95b/Java%20Setup%20on%20Linux%2036774edcda1343ae9bb9cfde10cdba6c)

[Docker Setup on Linux](Linux%20Setup%20on%20Azure%207100b190bfac4cc2a089ec436d50a95b/Docker%20Setup%20on%20Linux%20b60c631d0f0b40288a4bb64b6aac82c8)

[Kafka Setup on Linux](Linux%20Setup%20on%20Azure%207100b190bfac4cc2a089ec436d50a95b/Kafka%20Setup%20on%20Linux%2013001e06272949d8ab85130d54c98e62)

[VS Code Setup on Linux](Linux%20Setup%20on%20Azure%207100b190bfac4cc2a089ec436d50a95b/VS%20Code%20Setup%20on%20Linux%20e92fb84f2c914205bb007c42a40d0d98)

[Rust Setup on Linux](Linux%20Setup%20on%20Azure%207100b190bfac4cc2a089ec436d50a95b/Rust%20Setup%20on%20Linux%2060e78ad557de49dcbb2e1c36cf243ef8)

[Go Setup on Linux](Linux%20Setup%20on%20Azure%207100b190bfac4cc2a089ec436d50a95b/Go%20Setup%20on%20Linux%2048d8dc5ba5d34a538c2baee6dd935aef)