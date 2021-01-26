# LabTransfers
LabTransfer handles the hurdle of Corp -> RepLab Networking 

Working with James, we have an alternative for transfering files from our COE into the LAB this is substanitlly faster. This method has some requirements, but should work in most cases for our use, and safe us hours of time getting content onto our servers.

#Requirements :
Cygwin_x64
Filezilla, WinSCP or some SFTP Client
A server in the lab listening on port 22

#Setting up Cygwin...
Cygwin can be downloaded here : https://cygwin.com/setup-x86_64.exe
This installation is basically following through the wizard. When you get to the menu that allows you to install packages, search for SSH. We want to install both OpenSSH and SSH-Pagent as seen in the screenshot. This is a MUST! That is it for Cygwin.

#Setting up the SSH Tunnel...
Step 1 - Edit the "fwd-clean" string on line 13 to point to your Corpzone ID.
ex.) /bin/ssh -v -N -L "$1:$2:22" "corpzone\cspears1@DNVSSHGWESS01.CORPZONE.INTERNALZONE.COM"

Step 2 - Edit the "labTransfer.bat" file to point to your desired server in the lab that is listening on port 22. As well as the install location where the "fwd-clean" file is placed which is headed by "/cygdrive/c/...". Only make changes after "c/"
ex.) C:\cygwin64\bin\mintty.exe /cygdrive/c/Users/cspears1/Desktop/fwd-clean 55555 172.17.28.205

#Setting up the SFTP client...
The tunnel above allows traffic running over port 55555 from your localhost, TO the server in the lab. Within your cient of choice, the port will be "55555" (Or whatever you have defined in .bat script) and the host will be "localhost".

#Launching the tunnel...
Step 1 - Launch the "labTransfer.bat".
step 2 - You will be prompted for your Corpzone Password.
Step 3 - Duo Push to your phone by choosing option 1. (This is VERY quick)
Step 4 - The tunnel is now OPEN. If you close this terminal, your tunnel will close.

#Transfering the files...
Step 1 - Launch your SFTP client of choice, pointing to the varibles defined in the setup above.
Step 2 - You will be prompted for a password, this is the password  to login to the SERVER.
