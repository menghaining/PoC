## TYPE: Insufficient Session Expiration(CWE-613)
## Date: 5/12/2024

## Basic Information
+ Vendor: [cskefu](https://github.com/cskefu)
+ Homepage: https://github.com/cskefu/cskefu
+ **Affected Version**: v7.x, v8.x

## Tested on: Debian Linux

## Exploit Description
Although v7.x and v8.x had fixed similar [bug](https://github.com/cskefu/cskefu/issues/781), the bug still exists when access this application through REST API.
After admin deleting a logged-in user through calling REST API,  the user can still operate with the old session/authentication token.
The system is affected by CWE613-Insufficient Session Expiration, which indicates that previous sessions or authentication tokens tied to the old password remain valid and can still be utilized.

### PoC:
+ **V7.x**:
1. `admin` login through REST API;
   <img width="1016" alt="image" src="https://github.com/menghaining/PoC/assets/32480426/ac6d7b09-52fe-4411-bc2b-58958af988c4">

2. `admin` list all users through REST API;
   <img width="1023" alt="image" src="https://github.com/menghaining/PoC/assets/32480426/877d2954-5782-474c-933f-ff326c4f46dc">

3. `user1` login through web or REST API.
   <img width="1332" alt="image" src="https://github.com/menghaining/PoC/assets/32480426/839c26d8-3b6c-4492-8aa9-30bc56c677c6">

4. `admin` delete `user1` through REST API;
   <img width="1017" alt="image" src="https://github.com/menghaining/PoC/assets/32480426/19fd819a-fb05-41f9-8aaa-1af53321ac6d">

5. `user1` can still operate successfully like deleting contacts.
   <img width="1332" alt="image" src="https://github.com/menghaining/PoC/assets/32480426/1e9165c1-81f6-4118-be49-28e09f721178">
   <img width="1315" alt="image" src="https://github.com/menghaining/PoC/assets/32480426/b45a3913-0bf1-4448-adda-4fe02eb7a962">


+ **V8.x**
  + Since v8.x is not free for more than 2 users, we did code auditing and found it is the same as v7.x, which means this version also suffers from such a bug.
  + <img width="906" alt="image" src="https://github.com/menghaining/PoC/assets/32480426/9e393278-27a6-4235-aacc-575f51b3fa72">
  + https://github.com/cskefu/cskefu/blob/250e1d56a5c11cadd5017d2fe30e8f62afdf3980/contact-center/app/src/main/java/com/cskefu/cc/controller/api/ApiUserController.java#L317

https://github.com/cskefu/cskefu/issues/1019
