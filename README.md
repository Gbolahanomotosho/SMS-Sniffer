# SMS-Sniffer 

This is an sms sniffing tool which capture sms of any cellphones around you and it also allow you to view sms text on any device including the sender, the reciever, the date and time the sms text was sent and also save the result in sqlite file called (sms_result.db)


It also use a python library called (pyshark) for the network protocol analyzer which can be use in place of wireshark which makes it easier to capture/sniff gsm_sms data packet for those who not have much knowledge about gsm packets capturing


I will advise you to learn more about GSM Networking and GSM sniffing and how it works before using this tool

  
# Requirements

- linux operating system (Kali linux, Ubuntu 20.04, Dragon focal os, Ubuntu jammy jellyfish) with GNU 


- SDR (Software Define Radio) receiver hardware and software (Hackrfone great scott gadget, Bladerf, Limerf, RTL-SDR)

# Installation of SDR 


To install the hackrfone SDR on your pc (debian based and ubuntu precisely) 

Type 

sudo apt-get install hackrf

OR

If you want to install it from source and build it using package manager or build system which is highly recommmended for most users 

Type

git clone https://github.com/greatscottgadgets/hackrf.git

cd hackrf/host
mkdir build
cd build
cmake ..
make 
sudo make install
sudo Idconfig

Now type 

hackrf_info

To check your hackrf full info

# For gr-gsm

You will need to install gr-gsm(Generic Radio GSM) :  (For receiving GSM signal)


# Command

sudo add-apt-repository -y ppa:ptrkrysik/gr-gsm
sudo apt update
sudo apt install gr-gsm


If gr-gsm failled to setup then follow this link : https://github.com/ptrkrysik/gr-gsm/wiki/Installation 

To install Kalibrate : (For Frequency Calibration)

Type

apt-get install kalibrate-rtl

OR Type

sudo apt install build-essential libtool automake autoconf librtlsdr-dev libfftw3-dev
git clone https://github.com/steve-m/kalibrate-rtl
cd kalibrate-rtl
./bootstrap && CXXFLAGS='-W -Wall -O3'
./configure
make
sudo make install


# Usage 

You will use kalibrate to get all your near gsm base stations frequencies

Now open two terminals

On terminal 1 type this:

kal -s GSM900

It will show you something like this:

kal: Scanning for GSM-900 base stations.
GSM-900:
	chan: 13 (949.0MHz + 230Hz)	power: 4475698.89
	chan: 16 (954.5MHz + 223Hz)	power: 4849353.86


OR
 
If you dont want to use kalibrate You can also use gr-gsm to get all your near gsm base stations frequencies 
to get all your near gsm base stations frequencies with gr-gsm if you dont want to use kalibrate 

Just Type

grgsm_scanner -v -b GSM900

It will show you something like this

Scanning GSM900 frequencies...

Frequency: 935.3 MHz
    cell ID: 123456
    signal strength: -75 dBm


Frequency: 936.4 MHz
    cell ID: 789012
    signal strength: -83 dBm


Frequency: 937.6 MHz
    cell ID: 345678
    signal strength: -77 dBm



Now you need to capture gsm traffic using gr-gsm on frequency of your any gsm base station which you get from using kalibrate or gr-gsm 

Type 

grgsm_livemon -f <your_gotten_frequency>M

e.g

grgsm_livemon -f 949.0M

Ensure that you get these below result output on your terminal

15 06 21 2b 00 2b 01 f0 2b 2b 2b 2b 2b 2b 2b 2b 2b 2b 2b 2b 2b 2b 2b
15 06 21 2b 00 2b 05 2b 2b 08 2b 2b 2b 2b 2b 2b 2b 00 2b 2b 2b 40 2b
25 06 21 2b 00 2b 01 2b 2b 2b 2b 2b 7b 2b 2b 2b 2b 2b b2 2b 2b 2b 2b
15 06 21 2e 00 2b 01 2b 2b 2b 2b 2b 2b 2b 2b 00 2b 2b 2b 2b 2b 2b 2b

If you didnt get that following above 👆 output on your terminal then change frequency 


Now go to terminal 2 and type these command to run this tool to capture sms



git clone https://github.com/Gbolahanomotosho/SMS-Sniffer




cd SMS-Sniffer



unzip SMS-Sniffer.zip



cd SMS-Sniffer



pip3 install -r requirements.txt



python3 Sniffer.py



Then enter specific phone number you want to capture SMS


If there is none, you can press enter to skip


If sms text is encrypted then it wont capture the sms data packet, you will need a network analyzer tool like wireshark to decode the encrypted data packet 


You can learn more on how to use wireshark to capture, decode encrypted data packet


Decoding an encrypted data packet depends on the complexity or layer of the encryption, if it is a weak encryption like a cellphone device running on a 2g network then it data packet can be easily decoded


Though this tool has a python network protocol analyzer library called (pyshark) but it only help to capture/sniff the data packet, you can also learn how to use pyshark to decode an encrypted data packet in place of wireshark if you dont want to use wireshark


# Disclaimer



I wont be held responsible for any malicious use of this tool 


For educational purpose and ethical hacking only

You will solely responsible for any damage done with this tool







