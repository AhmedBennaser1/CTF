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

now access that page http://dev.titanic.htb ( don't forget to that to the /etc/hosts )

![image](https://github.com/user-attachments/assets/03e196cd-f145-4d4c-aae4-14710e9e9a27)

we can see that it uses gitea right here 

![image](https://github.com/user-attachments/assets/752ad44a-3ad6-4a7f-b34d-1e1fb85ee4b6)


so asking the AI he gave me the path for the config file 
![image](https://github.com/user-attachments/assets/f4f3c314-cf4a-41af-b019-dc2220a5d15e)


and like that we got a clie about a database file on the /data/gitea/gitea.db  

![image](https://github.com/user-attachments/assets/7f0b384a-fbe8-4032-9c59-0c64f974b473)

from that information i installed the database 
Command : <b> wget http://titanic.htb/download?ticket=../../../../../home/developer/gitea/data/gitea/gitea.db -O database </b>
![image](https://github.com/user-attachments/assets/98253aaa-5de7-43c0-a474-41385f8ad7d8)

So i have retrieved the hashed password ,  names ,  salts  using the following commad 


source = "https://0xdf.gitlab.io/2024/12/14/htb-compiled.html#"

Command : <b> sqlite3 database  "select passwd,salt,name from user" | while read data; do digest=$(echo "$data" | cut -d'|' -f1 | xxd -r -p | base64); salt=$(echo "$data" | cut -d'|' -f2 | xxd -r -p | base64); name=$(echo $data | cut -d'|' -f 3); echo "${name}:sha256:50000:${salt}:${digest}"; done | tee gitea.hashes </b> 

![image](https://github.com/user-attachments/assets/fbe6e924-c5db-457e-ba09-44a099693a34)

with that on i have tried to crack those hashes using hashcat 
Command : <b> hashcat gitea.hashes  --user /usr/share/wordlists/rockyou.txt</b>

![image](https://github.com/user-attachments/assets/d2ed5eb3-ebca-4c6a-bd26-2f57c9d634e0)

and with that i got the password for the developer and now the ssh works 
![image](https://github.com/user-attachments/assets/279b34fb-01de-47d1-a692-12b40fa864cf)

NOw the mission is to search for priv esc methods and searching through that they were no suid permissions or sudo for the developer  i've tried to see the listening ports but still nothing now i thought about going through the process executed by the developer 

![image](https://github.com/user-attachments/assets/8a24c2ac-a11b-4976-b158-614a3ccad2f5)

there was an intersting file app.py but there was nothing over there so searching around i found but the /images was writable by the developer 
Command : <b> find . -writable -user developer  2>/dev/null
![image](https://github.com/user-attachments/assets/7a8b7984-52bc-4246-b2d8-cfc1bc939d91)

which it does mean that we can run some scripts on that directory so searching around again i found a bash script 
![image](https://github.com/user-attachments/assets/0dc8ef9f-35ca-4267-8423-b09e66568d32)

it uses our writable directory and the magick command i thought that we may have vuln right here and checking the magick version i found that it was exploitable 

![image](https://github.com/user-attachments/assets/9ec2aa69-a692-4404-9926-354449142201)

![image](https://github.com/user-attachments/assets/d03fb4cd-001a-4b1b-82e3-18db9dc48c64)

So as y'all can remember that we had that writable directory which it leads that we can execute that over there 

![image](https://github.com/user-attachments/assets/7a89b6e8-799f-40d0-ba18-0593677acae2)

and after that you'll get your root flag Congrats 
