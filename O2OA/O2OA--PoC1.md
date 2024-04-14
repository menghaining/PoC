## TYPE: Insufficient Session Expiration(CWE-613)

## Date: 4/14/2024
## Product Information
### Vendor: [o2oa](https://github.com/mindskip)
### Homepage: https://github.com/o2oa/o2oa
**version**: 
9.0.3(Apr 3, 2024 )

## Tested on: Debian Linux, Mysql

## Exploit Description
Suffering from CWE613-Insufficient Session Expiration.
Have not expire user session after user changing his password or admin reset his password.
### PoC1
1. `admin` login
2. `user1` login
3. `admin` reset password of `user1`
   ![alt text](image1.png)
4. `user1` is not forced log out, and can still do anything like modify his information.
![alt text](image.png)
![alt text](image-1.png)

### POC2
1. `user1` login
2. `user1` change his password
![alt text](image-2.png)
![alt text](image-3.png)
3. `user1` can still operate any thing
![alt text](image-4.png)
![alt text](image-5.png)
![alt text](image-6.png)
