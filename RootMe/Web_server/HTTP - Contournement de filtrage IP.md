<h1>HTTP - Contournement de filtrage IP</h1>
<h4>Link For the challenge : https://www.root-me.org/fr/Challenges/Web-Serveur/HTTP-Contournement-de-filtrage-IP?action_solution=voir&debut_affiche_solutions=0#pagination_affiche_solutions</h4>

![image](https://github.com/user-attachments/assets/6eb8edc5-c4ef-4e13-bf1f-9f195ca8d7e4)


<h2>Contournement de filtrage IP vulnérable</h2>
After launching the challenge we land on this page 

![image](https://github.com/user-attachments/assets/4770ae33-cc2f-40ce-9411-dba15b9c444a)

As you can see on the image below it says that we don't belong to the Local area network (LAN) <br>
We can play with that with burpsuite changing the forward to a local area network 
<br>


We can Use on of those IPS to forward the traffic to us <br>
![image](https://github.com/user-attachments/assets/69de1ccf-9aab-4f8b-89f3-a7ac80bdd734)



So i capture the traffic using burpsuite and send it to the repeater : 

![image](https://github.com/user-attachments/assets/46ad19a8-e9c4-4f7c-8c34-c7660bb61dcc)

And as you can see i have added an additional header called X-Forwarded-For : 'An Ip from the image just before'<br>
And after sending the request we can see that he gave us  the password to validate the challenge <br>

<h2>Another Method (easier) </h2>
Using CURL by adding the X-Forwarded-For to the header using -H 

![image](https://github.com/user-attachments/assets/bb8ba828-7f72-439c-a135-8137ab4d665b)
