# bbrplus
BBRPLUS内核及安装

系统要求：Debian 8.0、Debian 9.0、CentOS 7.0

一、关闭原版BBR：

sed -i '/net\.core\.default_qdisc=fq/d' /etc/sysctl.conf && sed -i '/net\.ipv4\.tcp_congestion_control=bbr/d' /etc/sysctl.conf

sysctl -p


二、下载内核：

Debian x32:

wget https://raw.githubusercontent.com/binghe3337/bbrplus/master/kernel/Debian_8_9/x32/linux-headers-4.14.91_4.14.91-1_i386.deb

wget https://raw.githubusercontent.com/binghe3337/bbrplus/master/kernel/Debian_8_9/x32/linux-image-4.14.91_4.14.91-1_i386.deb

Debian x64:

wget https://raw.githubusercontent.com/binghe3337/bbrplus/master/kernel/Debian_8_9/x64/linux-headers-4.14.91.deb

wget https://raw.githubusercontent.com/binghe3337/bbrplus/master/kernel/Debian_8_9/x64/linux-image-4.14.91.deb


三、安装内核：

Debian x32:

dpkg -i linux-headers-4.14.91_4.14.91-1_i386.deb

dpkg -i linux-image-4.14.91_4.14.91-1_i386.deb

Debian x64:

dpkg -i linux-headers-4.14.91.deb

dpkg -i linux-image-4.14.91.deb


四、更新引导：

/usr/sbin/update-grub


五、删除旧内核：

查看当前系统所有内核

dpkg -l|grep linux-image | awk '{print $2}'

卸载其余内核

apt-get purge -y 其余内核名称


六、更新引导：

/usr/sbin/update-grub


七、重启：reboot


八、启用BBRplus:

echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf

echo "net.ipv4.tcp_congestion_control=bbrplus" >> /etc/sysctl.conf

sysctl -p


九、重启：reboot

