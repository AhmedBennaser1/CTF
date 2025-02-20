<h1>Hack the BOX </h1>
<h3>Titanic ( Linux - easy ) </h3>
![image](https://github.com/user-attachments/assets/a3d9d207-6602-459a-bed8-590c80a3005f)

 As every box or machine you deploy I've started with basic nmap scan 

 Command : <b> nmap -p- {ip} --min-rate 10000 </b> 
![image](https://github.com/user-attachments/assets/372b5deb-7b52-4a25-943e-f49ba821489d)

 after having the idea of open ports we add -sCV for the scripts and versions running on the active ports 
Command  : <b> nmap -p 22,80  10.10.11.55  --min-rate 10000 -sCV -oA titanic </b>
