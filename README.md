Documentation about the setup of the WaaS training course 7th of June 2018

The course will be given in the v114 room at PSB Ghent.

Trainer and organiser: 
Alexander Botzki alexander.botzki@vib.be, 
local tech support christof.debo@vib.be

Cloud provider:  Technical support: jarno.laitinen@csc.fi 

When?
Test VM was setup on 8.2.2018

Resource:  ELIXIR -FI , cPouta IaaS cloud.

Resource allocation:
For testing a 4 core, 15 GB virtual machine was created.

Software environment: 
Ubuntu 16.04. The image was available from cPouta. 

Further installation steps:

for CentOS:
- VM: yum install x2goserver
- VM: yum groupinstall Xfce
- cPouta Web UI: Assign a Floating IP - this has already been done by Jarno
- cPouta Web UI: Open port 22/TCP - - this has already been done by Jarno
- Your local workstation: Install x2go client, create x2go session for Xfce desktop towards Floating IP

or our setup on the Google Cloud on Ubuntu


do we need to execute the standard update steps of Ubuntu?
$ sudo apt-get update
$ sudo apt-get upgrade


then:
´´´
#!/bin/bash
apt-get install -y mc xinetd tigervnc-standalone-server lightdm unity-greeter ubuntu-desktop
for i in `seq 1 1`;
do
    useradd -m "VIBTraining$i" -s /bin/bash
    echo "VIBTraining$i:TrainingVIB$i" | chpasswd
    usermod -G admin "VIBTraining$i"
done
update-rc.d xinetd enable
update-rc.d lightdm enable
cp -R etc/* /etc/
cp -R usr/* /usr/
glib-compile-schemas /usr/share/glib-2.0/schemas/
/etc/init.d/xinetd restart
/etc/init.d/lightdm restart
cd /home
chmod 750 *
´´´

Check also:

Open up the ‘Software & Updates’ tool from the Unity Dash
Click the ‘Additional Drivers’ tab
Follow any on-screen prompts to check for, install and apply any changes 
