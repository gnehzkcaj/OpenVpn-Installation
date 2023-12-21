# OpenVpn-Installation
Latest installation Guide in AWS Ubuntu

To determine operating system:
```
cat /etc/issue
lsb_release -a
uname -a
```

# Step 1:
Launch AWS Ubuntu EC2. Inbound rules allow port 22, 443, 943, 1143, 1194 by Openvpn default.
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
  =>port for Web UI 943 
  =>443
  =>Activation Key leave blank
```

# Step 3:

Set up in browser: https://[your AWS public ipaddress]:943/admin
Configuration=>Network Settings=>IP Address=>[your AWS public ipaddress]

# Step 4:
Update -> CONFIGURATION -> Network Settings -> Hostname or IP Address: (Change to AWS public address)

DOWNLOAD User Profiles from USER MANAGEMENT

# Ref:
1. Access Server Quick Start Guide (https://openvpn.net/quick-start-guide/)
2. Software Packages for Ubuntu (https://as-portal.openvpn.com/get-access-server/ubuntu)
3. Finishing Configuration of Access Server (https://openvpn.net/vpn-server-resources/finishing-configuration-of-access-server/)
4. Set up a Linux VPN Server Using OpenVPN: Connecting to Devices and Managing VPN (https://www.hostinger.com/tutorials/how-to-set-up-a-linux-vpn-server-with-openvpn/)
5. How do I install an SSL certificate for my website on my EC2 Linux Ubuntu instance? (https://repost.aws/knowledge-center/ec2-linux-ubuntu-install-ssl-cert)
