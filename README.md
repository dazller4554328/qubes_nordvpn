NordVPN Auto-Connect Service for Qubes OS (sys-vpn)
This service automates the connection to NordVPN in a sys-vpn qube using fedora-40-xfce as the template. It ensures that NordVPN is connected with specific security settings (killswitch, CyberSec, LAN discovery, and notifications) whenever the sys-vpn qube starts.

Configuration Instructions:

Create the Service File

Open the service configuration file:

sudo nano /etc/systemd/system/nordvpn-auto.service

paste the contents of the nordvpn-auto.service:

Replace "NORDVPN-TOKEN" with your actual NordVPN login token.

Activate the Service

Reload the systemd manager configuration:

sudo systemctl daemon-reload

Disable the service to prevent auto-start outside sys-vpn:

systemctl disable nordvpn-auto.service

Set Up the Qube

Create the sys-vpn qube using fedora-40-xfce as the template.

Configure rc.local in sys-vpn

Edit the rc.local file to start the service at qube boot:

sudo nano /rw/config/rc.local

Add this line at the end of the file:

systemctl start nordvpn-auto.service

Network Configuration

Ensure sys-vpn is configured in the network chain: sys-vpn -> sys-firewall -> sys-net.

This setup ensures NordVPN automatically connects and enforces essential security settings each time the sys-vpn qube starts.





