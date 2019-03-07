# bbrplus
BBRPLUS内核及安装

安装内核：

dpkg -i linux-headers-${kernel_version}.deb

dpkg -i linux-image-${kernel_version}.deb


删除旧内核：


更新引导：


重启：reboot


启用BBRplus:

echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf

echo "net.ipv4.tcp_congestion_control=bbrplus" >> /etc/sysctl.conf

sysctl -p


重启：reboot

