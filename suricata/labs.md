# Suricata Labs
> Date: 2026-06-04

## Lab 1 - Interface Configuration
i downloaded suricata in my kali linux machin
to start suricata and stop it the command you need is systemclt start suricata or systemclt stop suricata
 and status to check its curent states 
 
 <img width="1912" height="741" alt="image" src="https://github.com/user-attachments/assets/9db5a5c9-8d88-479c-bfd4-017e8ea734a2" />

# next step
i found the file using ls -al /etc/suricata

<img width="344" height="107" alt="image" src="https://github.com/user-attachments/assets/c0e001a6-4ce6-475f-bc96-7b370b76ef8a" />

# next step conigure 
i started by specifying which home net the suricata will be set up i got that ip address for my home network using ip a or ifgonfig command and
changed the settings in suricata

<img width="419" height="358" alt="image" src="https://github.com/user-attachments/assets/1f162c38-dc32-4bfa-a3be-31ac11c6c1c8" />

next i checked in my interface was okay by searching /af-packet and confiremed its te same as the ip a address one 

<img width="506" height="272" alt="image" src="https://github.com/user-attachments/assets/a09d8b9c-41e5-482f-9f21-2d790d9d037f" />

moving on i updated the suricata to get the rules ready 

<img width="724" height="397" alt="image" src="https://github.com/user-attachments/assets/cacf2672-618e-44aa-bb59-f60874579979" />

next i use suricata-update list-sources to see the list of rules available 

<img width="1115" height="786" alt="image" src="https://github.com/user-attachments/assets/c0f87cc4-0c6c-4cf5-95be-f322d8deeddd" />

next steo is setting it to run in the background with -v as verbose 


<img width="1867" height="400" alt="image" src="https://github.com/user-attachments/assets/8764432a-48f7-42b6-b030-ecd5608e8545" />


lastly we start running our suricta by start surticata service 

<img width="1564" height="475" alt="image" src="https://github.com/user-attachments/assets/684f8146-6972-48b9-9ac0-384e26e34fe5" />


<img width="386" height="119" alt="image" src="https://github.com/user-attachments/assets/7acc33aa-1643-45dd-adfb-e8016490fc94" />

the fast.jason file and eve.json will show incase of any intrusion they each provide different formats 


### next i want to run a simple test to see if the suricata is capturing files 

i do that by typing 

<img width="286" height="47" alt="image" src="https://github.com/user-attachments/assets/e5500078-3e2d-4201-ba5c-27c2a21d2c01" />

this simply test my network intrusion detection 

<img width="956" height="378" alt="image" src="https://github.com/user-attachments/assets/b32a5c35-1c26-4cd2-a62e-6aae2a832fea" />

well and good our ids is running in the back ground and capturing 

next step i decided to create my own rule ei first created a file using vim /etc/suricata/rules/local.rules

oi then set my first rule to alert for any icmp pings 

<img width="970" height="67" alt="image" src="https://github.com/user-attachments/assets/8948f777-d68d-4d60-bc0e-a524f9784586" />

and and to connect my local.rules i went to configure it in the surivata.yaml file under rule-path

<img width="919" height="439" alt="image" src="https://github.com/user-attachments/assets/d09b1615-e81e-48fa-abd2-44bfb59dd446" />

to test it i ran icmp ping packets into my home router and checked if it had captured and alterted me 

<img width="829" height="337" alt="image" src="https://github.com/user-attachments/assets/14e63092-abae-46af-a624-24bd3031cb0d" />

and when i opened suricata to see if it has captured it did and here are the rsults

<img width="1912" height="475" alt="image" src="https://github.com/user-attachments/assets/cec4bd4a-759c-4fa7-8134-cf009bd1fec5" />


