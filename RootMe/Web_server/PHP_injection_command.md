
challenge link:  http://challenge01.root-me.org/web-serveur/ch54/index.php 

PHP - Injection de commande

10 Points  
Service de ping v1

![image](https://github.com/user-attachments/assets/2ea6aaf8-e57a-460d-9283-9308eee6c6cf)


So starting with testing some injection like ;cat ls to see if we have the flag on our current directory 

![image](https://github.com/user-attachments/assets/fcbcc630-2b92-4bc0-8414-8e3f0fd2f0bb)

BUt nothing intersting with that i saw the hint given by the challenge that we need to read the index.php

![image](https://github.com/user-attachments/assets/2eae4564-1dbb-450d-8e0c-fa2b385aabd2)



But it wasn't showing anything 
![image](https://github.com/user-attachments/assets/b06c9faf-ce86-44b0-9a1b-cbd1eceff0b9)


so i've thought since it is php  injection it's gotta be  executing the script when i cat it with that on i've tried to cat just the flag
![image](https://github.com/user-attachments/assets/7ba4f636-e866-4dda-b637-2605e481f859)


and it worked since the content of the flag is in the .passwd file the rest is easy 

![image](https://github.com/user-attachments/assets/ead32fd1-ee85-4758-b942-1f7f94382c06)

flag:S3rv1ceP1n9Sup3rS3cure



