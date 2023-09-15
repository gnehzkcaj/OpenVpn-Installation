# OpenVpn-Installation
Latest installation Guide in AWS Ubuntu

# Step 1:
Lauch AWS Ubuntu EC2. Inbound rules allow port 22, 443, 943, 1143, 1194 by Openvpn default.
Port for VPN client connections: tcp/443, udp/1194
# Step 2:
```
sudo -s
apt update && apt -y install ca-certificates wget net-tools gnupg
wget https://as-repository.openvpn.net/as-repo-public.asc -qO /etc/apt/trusted.gpg.d/as-repository.asc
echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/as-repository.asc] http://as-repository.openvpn.net/as/debian jammy main">/etc/apt/sources.list.d/openvpn-as-repo.list
apt update && apt -y install openvpn-as
systemctl status openvpnas.service
ovpn-init --force
  =>agreement=>yes
  =>primary access server=>yes
  =>(2) ip address Admin Web UI, choose default
  =>rsa
  =>2048
  =>943 
  =>443
  =>Activation Key leave blank
```

# Step 3:

Set up in browser: https://[your AWS public ipaddress]/admin
Configuration=>Network Settings=>IP Address=>[your AWS public ipaddress]


# Ref:
1. Access Server Quick Start Guide (https://openvpn.net/quick-start-guide/)
2. Software Packages for Ubuntu (https://as-portal.openvpn.com/get-access-server/ubuntu)
3. Finishing Configuration of Access Server (https://openvpn.net/vpn-server-resources/finishing-configuration-of-access-server/)
4.
