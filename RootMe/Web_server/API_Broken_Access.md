link challenge : https://www.root-me.org/fr/Challenges/Web-Serveur/API-Broken-Access



API - Broken Access
15 Points  
Suivez le Swagger 



![image](https://github.com/user-attachments/assets/089e7039-4e8f-4c9f-b158-3206eff77c2d)


By starting the challenge we get an API interface with intersting informations 

![image](https://github.com/user-attachments/assets/a4583b0f-f428-4eac-bab1-3c39a494726f)

so throught this i knew nothing about it, I've started by signup a new user

![image](https://github.com/user-attachments/assets/02c3f17b-f8dd-4b9b-8e75-6ac4bda4ee17)

![image](https://github.com/user-attachments/assets/2b82558c-9fc8-4097-8b7c-689e0a9cc1a8)


And then i tried loggin in the the application using the new user 

![image](https://github.com/user-attachments/assets/3470b908-8074-479b-9235-16dbd33b9ef6)
![image](https://github.com/user-attachments/assets/13f10c3d-013e-4929-b725-b95eb29cf54f)

Now i saw interesting api the user one i've tried executing that and it prints a response with the userid ,  username and the note 
![image](https://github.com/user-attachments/assets/2f782f07-add5-40e7-9536-8adef0d828e1)


I've connected to the url requested by the api with that on i've tried some url injection 

![image](https://github.com/user-attachments/assets/68905b92-2ed4-4701-8c64-1257c2df91db)

But it didn't worked
![image](https://github.com/user-attachments/assets/7167f470-d022-43ff-b1fb-a69549d4c103)


with that on it was pretty simple 
by just executing the url/api/user/id_number you'll get the flag on the userid=1 of admin

![image](https://github.com/user-attachments/assets/cd09169a-ba8a-40f2-9812-7851ad3a209a)


flag=RM{E4sy_1d0r_0n_API}


