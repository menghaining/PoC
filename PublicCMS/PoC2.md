## TYPE: Insufficient Session Expiration(CWE-613)

## Date: 8/5/2024
## Vendor
[sanluan](https://github.com/sanluan)

Homepage: https://github.com/sanluan/PublicCMS

version: v4.x (published at May 30, 2023 at 2:26 pm)

docker: https://hub.docker.com/layers/sanluan/publiccms/latest/images/sha256-9677a5a75f98d9c1802bb9d889bf160b587b528c5d071e88015f651cdaf523f8?context=explore

## Tested on: Debian Linux

## Exploit Description
Suffering from CWE613-Insufficient Session Expiration. 
When the admin disables the user, the application does not expire the user's session. 
As a result, when the admin enables the user again, the user can use the old session to operate successfully!

### PoC
1. `admin` login and list the user list
   <img width="1431" alt="image" src="https://github.com/user-attachments/assets/13fb4454-1755-4314-aa03-d1a4a088964e">

2. `user3` login with the session shown below:
   <img width="1373" alt="image" src="https://github.com/user-attachments/assets/074db6f0-9790-4ac0-a161-0642399da9b2">
   
3. `user3` list all users:
   <img width="1341" alt="image" src="https://github.com/user-attachments/assets/16fe5b8f-c96b-4edb-9e64-e0da4eb78d5f">
   <img width="1392" alt="image" src="https://github.com/user-attachments/assets/40df46c4-2ca5-4f29-9272-768c85e00d50">

4. `admin` disable  `user3`
   <img width="1429" alt="image" src="https://github.com/user-attachments/assets/76a9914d-0c16-4805-9b49-680647e6d0b3">

5. 1 min later, `admin` enable `user3`
   <img width="1427" alt="image" src="https://github.com/user-attachments/assets/453944e2-45a0-4859-83a6-c7808e2be363">
   
6. `user3` can still operate with old session:
   <img width="1338" alt="image" src="https://github.com/user-attachments/assets/1acab892-ebb5-4a29-978e-7bdae649221e">
   <img width="1386" alt="image" src="https://github.com/user-attachments/assets/22582302-a723-44c7-935d-212de706418c">

7. `admin` refresh the user list
   <img width="1435" alt="image" src="https://github.com/user-attachments/assets/7829106f-e808-4f84-88f2-11dcf2b06a95">


