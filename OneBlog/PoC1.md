## TYPE: Insufficient Session Expiration(CWE-613)

## Date: 8/4/2024
## Vendor
Github: [zhangyd-c](https://github.com/zhangyd-c)
Gitee: [yadong.zhang](https://gitee.com/yadong.zhang)
### Homepage: 
https://github.com/zhangyd-c/OneBlog

https://gitee.com/yadong.zhang/DBlog

**version**: 
v2.3.4

## Tested on: Debian Linux

## Exploit Description
The user can continue to operate with the old sessionId after the admin changes the user's password.
Suffering from CWE613-Insufficient Session Expiration.

### PoC
1. `admin` login
2. `user1` login success and the sessionid is shown below
 <img width="1432" alt="image" src="https://github.com/user-attachments/assets/cc79e0a4-d0af-4e71-ae3b-947efb047cc8">

3. `admin` change the password of `user1`
   <img width="1341" alt="image" src="https://github.com/user-attachments/assets/0ea0cccf-5589-44c4-8663-59ad7d710ff0">
   <img width="1117" alt="image" src="https://github.com/user-attachments/assets/3064c65e-6b6a-4067-92dc-349d366edfc9">

4. `user1` can still operate using old sessionid, like modify comment
   <img width="1423" alt="image" src="https://github.com/user-attachments/assets/d2cf7ec9-a749-4b8c-9098-af9331b16784">
