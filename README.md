# T2U-plus-kali-installation
The following steps are for what I did in order to install and successfully run T2U Plus in Kali Linux (Kali 2023.1) 

![image](https://github.com/VSQACE34/T2U-plus-kali-installation/assets/87938890/baaf73cf-5807-466e-98a4-6052e15f104f)

 ☝️ This is the antenna in discussion

So like others, I had initial troubles with kali not being able to recognize T2U Plus. 
I followed the initial steps of the GitHub repository mentioned here in this link https://github.com/nlkguy/archer-t2u-plus-linux
for ease I will write the codes that I followed below, directly copying from the link

" Driver for Debian Based Linux Distros (Ubuntu/Kali Linux)(x86_64)

  Update the package information :

    sudo apt update

  Install dkms and git :

    sudo apt install dkms git

  Install Build Dependencies :

    sudo apt install build-essential libelf-dev linux-headers-$(uname -r)

  Download the Driver files using git :

    git clone https://github.com/aircrack-ng/rtl8812au.git

  Navigate to the Downloaded directory :

    cd rtl88*

  Install the Driver

    sudo make dkms_install

if the installation is aborted, check existing dkms modules and uninstall the previously installed driver

👉 Uninstall Existing Driver

    Check the wireless interfaces by typing iwconfig.


Now keep in mind that I am doing the process for Kali Linux on PC (specifically Kali Linux live) only. I haven't tried this for Raspberry Pi or any other OS systems

Now after following this much I faced the trouble that the "dkms" package wasn't getting updated/installed even though I was doing the sudo apt-get update

after searching through the internet to find out the reason for this, I finally found this article. 
https://superuser.com/questions/1410570/cant-install-anything-on-kali-linux-unable-to-locate-package

and having read through this article, I found the issue can be solved by just using the code below
(Note: the command below is copied directly from the Kali rolling repository using the link https://docs.kali.org/general-use/kali-linux-sources-list-repositories)


    echo "deb http://http.kali.org/kali kali-rolling main contrib non-free non-free-firmware" | sudo tee /etc/apt/sources.list

after this, the dkms package was installed correctly and the sudo make dkms_install code was run. 
At first, the OS still couldn't recognize the T2U plus antenna. But a quick reboot solved the problem. 


This is my first time writing a documentation process hope this helps. 

I think I will upload a txt file with the commands in serial order. Just download the txt file, followed by doing a 

sudo chmod +x rt_file

and then just execute the file by 
./rt_file
