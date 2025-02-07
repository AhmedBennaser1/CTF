Link to the challenge : [https://www.root-me.org/fr/Challenges/Web-Serveur/HTML-Code-source](https://www.root-me.org/fr/Challenges/Web-Serveur/HTTP-Open-redirect)


HTTP - Open redirect
10 Points  
Internet est si vaste

![image](https://github.com/user-attachments/assets/6fffad42-32e4-464d-bc16-4c53b43b1e5a)

I've started by intercepting the traffics with burp 


![image](https://github.com/user-attachments/assets/115176ae-1228-4bce-99ca-b78ab5269267)

so we can see that our url is https://facebook.com : i've tried to redirect this for example to google.com

![image](https://github.com/user-attachments/assets/427ba4a0-3eb2-40df-a8fe-84c6f10321e2)

so by that it means that we need to change the hash i've used a hash generator to compare the md5 hash of the url and the 
hash intercepted finding its the same hash (https://www.md5hashgenerator.com/)

![image](https://github.com/user-attachments/assets/c19cb07f-fe78-47fa-b41d-cafd39ae7640)

so using that to regenerate the hash for the new url we got the flag 

![image](https://github.com/user-attachments/assets/dd82119f-9519-4080-b402-f576553a31e4)


flag:e6f8a530811d5a479812d7b82fc1a5c5  




