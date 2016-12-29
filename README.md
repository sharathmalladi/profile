## Connect to Linux VM using Remote Desktop

### Helpful links:
https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-linux-classic-remote-desktop
https://channel9.msdn.com/Blogs/raw-tech/How-to-RDP-to-your-Linux-desktop-in-Azure

sudo apt-get update  
sudo apt-get install lxde  
sudo apt-get install xrdp  
echo lxsession -s LXDE -e LXDE > ~/.xsession  
sudo /etc/init.d/xrdp start  
Open port 3389 in Azure firewall as follows:  
Connect to VM on Azure Portal -> Network Interfaces -> Network security group -> Inbound security rules -> Add rule to allow port 3389.  

Then remote desktop from Windows to the linux machine  

### Troubleshooting steps:  
Try the following if the above does not work:  
sudo service xrdp restart  
Ensure you are using the Module called 'sesman-Xnvc' when connecting.  
