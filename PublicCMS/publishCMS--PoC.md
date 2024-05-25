## TYPE: Insufficient Session Expiration(CWE-613)

## Date: 4/2/2024
## Vendor
[sanluan](https://github.com/sanluan)

Homepage: https://github.com/sanluan/PublicCMS

version: v4.x (published at May 30, 2023 at 2:26 pm)

docker: https://hub.docker.com/layers/sanluan/publiccms/latest/images/sha256-9677a5a75f98d9c1802bb9d889bf160b587b528c5d071e88015f651cdaf523f8?context=explore

## Tested on: Debian Linux, Mysql

## Exploit Description
Suffering from CWE613-Insufficient Session Expiration. 
When the user changes his password, the system will let the user log in again. However, when the admin changes the user's password, the system does not redirect to the login page, which leads to the user still operating until the current session timeout.

### PoC
1. `admin` login
2. `user1` login
3. `admin` change the password of  `user1`
4. `user1` can still operate, like change his information

PoC video: https://1drv.ms/v/s!AmTWEcd1YDpUjgoJ8lkA8pN8zYEJ?e=gIlbGf
