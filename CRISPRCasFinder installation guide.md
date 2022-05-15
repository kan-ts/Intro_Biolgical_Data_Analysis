# CRISPRCasFinder installation guide
Update for 2022
This document is intented as a guide for installation of CRISPRCasFinder version 4.2.20 from source with its dependencies. For complete guide, please refer to user manual.

## Download source file 
1. download source file from [CRISPRCasFinder website](https://crisprcas.i2bc.paris-saclay.fr/Home/Download) by downloading the [CRISPRCasFinder standalone version](https://crisprcas.i2bc.paris-saclay.fr/Home/DownloadFile?filename=CRISPRCasFinder.zip) and its manual

## Extract the zip file
2. extract the CRISPRCasFinder zip file using Windows program or use **unzip** command in Linux(wsl), you may need to install it using apt
```
sudo apt install unzip
unzip CRISPRCasFinder.zip
```

## Change installer scripts
3. Open **installer_UBUNTU.sh** file in **CRISPRCasFinder-release-4.2.20** folder using text editor (i.e. Notepad++ or Sublime Text)

4. delete line 96-106 (to install Macsyfinder by ourself) and save it
```
#install macsyfinder
.
.
.
   echo "export MACSY_HOME=${CURDIR}/macsyfinder-1.0.5/" >> $HOME/.profile
```


## Install MacSyFinder
5. install Macsyfinder version 1.0.5 using package manager
```
sudo apt install macsyfinder
```
**If step 5 is not working,i.e. no package available do install from source**

Download the Macsyfinder version 1.0.5 from [here](https://github.com/gem-pasteur/macsyfinder/tree/macsyfinder-1.0.5)
Extract the zip and proceed with the installation as recommend in its readme.md file with slight modification which are
* replace version (macsyfinder-x.x) in to macsyfinder-1.0.5
* replace "python" with "python2.7", you may need to install python2.7 beforehand (using sudo apt install python2.7
* when run the test in step 4 (macsyfinder/readme.md), you may see lot of errors, don't worry, It may work just fine. just proeed to step 6 of this guide.


6. try using macsyfinder
```
>macsyfinder --help
```

7. add Macsyfinder directory to profile
```
export MACSY_HOME=/usr/bin/ >> ~/.profile
source ~/.profile
```

## Install CRISPRCasFinder.sh
8. copy the folder **CRISPRCasFinder-release-4.2.20** to your desire location (preferably make a folder name program in ~ directory)
```
mkdir ~/program
cp -r *current_dir*/CRISPRCasFinder-release-4.2.20 ~/program/
```
9. go to ~/program/CRISPRCasFinder-release-4.2.20
```
cd ~/program/CRISPRCasFinder-release-4.2.20
```

10. run the **installer_UBUNTU.sh** that has been edited
```
bash installer_UBUNTU.sh
source ~/.profile
```

you may have to wait hours or so until the installation is completed.

11. test the install program
when the installation is complete, test the install program using following command (run in CRISPRCasFinder folder)
```
perl CRISPRCasFinder.pl -in install_test/sequence.fasta -cas
```

If some error happen, try resolve it by yourself first or ask me for assistant


## Testing and troubleshooting


