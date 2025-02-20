<h1>Hack the BOX </h1>
<h3>Titanic ( Linux - easy ) </h3>

![image](https://github.com/user-attachments/assets/a3d9d207-6602-459a-bed8-590c80a3005f)

 As every box or machine you deploy I've started with basic nmap scan 

 Command : <b> nmap -p- {ip} --min-rate 10000 </b> 
![image](https://github.com/user-attachments/assets/372b5deb-7b52-4a25-943e-f49ba821489d)

 after having the idea of open ports we add -sCV for the scripts and versions running on the active ports and -oA to save the output of our nmap scan 
Command  : <b> nmap -p 22,80  10.10.11.55  --min-rate 10000 -sCV -oA titanic </b>

![image](https://github.com/user-attachments/assets/6086ab21-92b2-4ae0-ac30-4645f47cd77b)

so we can see on the scan that we have an http server ( web page ) that's why we have to add the related domain name to the ip in the <b> /etc/hosts </b>

![image](https://github.com/user-attachments/assets/b126f239-202d-4d74-bbf6-0573d239c25e)

after that you can successfuly access the web page 

![image](https://github.com/user-attachments/assets/79a5f422-4401-4b20-b201-e804e3e1d9af)

I've tried to access some common files like robots.txt searching for hints but it didn't worked 
after clicking on the intersting button "book your trip" 

![image](https://github.com/user-attachments/assets/0449b478-5465-429b-ab36-805f3e869211)

i saw that we need to submit some informations 
so that's why i've started intercepting the traffic for some information and maybe for attacks 

![image](https://github.com/user-attachments/assets/4a9af474-2298-4a32-936d-15637767a761)

i've tried to sql inject that but it didn't worked that's why when i have forwarded again i've seen something intersting and familiar that i've already encountered

![image](https://github.com/user-attachments/assets/7ee62446-a043-46a3-b228-585b4560fe30)

seems like we can't get some files using an LFI attack  and it's was a success 
![image](https://github.com/user-attachments/assets/b8c45ff0-3aba-4c68-ad72-17dd4cbedac2)

after that i've searched for active users and seemed like developer was the user so i've tried to access the flag using those information and same it was a success 

![image](https://github.com/user-attachments/assets/d918ab2c-924c-449f-87f1-24bebb519817)

after that i had no clue what i'm going to do to access the developer on ssh i've needed just a clue for the path for some config file so i've tried to search for some maybe existing subdomains 

![image](https://github.com/user-attachments/assets/928445bc-b7f0-4bc5-8625-60c8cfbd27e9)
![image](https://github.com/user-attachments/assets/ad7a351c-58cb-4b3a-af24-17836abd434f)
