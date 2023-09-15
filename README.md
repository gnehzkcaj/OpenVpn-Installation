# OpenVpn-Installation
Latest installation Guide in AWS Ubuntu

# Step 1:
```
sudo -s
apt update && apt -y install ca-certificates wget net-tools gnupg
wget https://as-repository.openvpn.net/as-repo-public.asc -qO /etc/apt/trusted.gpg.d/as-repository.asc
echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/as-repository.asc] http://as-repository.openvpn.net/as/debian jammy main">/etc/apt/sources.list.d/openvpn-as-repo.list
apt update && apt -y install openvpn-as
systemctl status openvpnas.service
ovpn-init
```

# Ref:
1. Access Server Quick Start Guide (https://openvpn.net/quick-start-guide/)
2. Software Packages for Ubuntu (https://as-portal.openvpn.com/get-access-server/ubuntu)
3. Finishing Configuration of Access Server (https://openvpn.net/vpn-server-resources/finishing-configuration-of-access-server/)
4.
