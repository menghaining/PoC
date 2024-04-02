## TYPE: Insufficient Session Expiration(CWE-613)

## Date: 4/2/2024
## Vendor
[sanluan](https://github.com/sanluan)
Homepage: https://github.com/sanluan/PublicCMS
version: latest (published at May 30, 2023 at 2:26 pm)

## Tested on: Debian Linux, Mysql

## Exploit Description
Suffering from CWE613-Insufficient Session Expiration. 
When user change his password, system would let the user login again.
However, when admin change user's password, system do not redirect to login page, which lead to the user can still operate until current session timeout.

### PoC
1. `admin` login
2. `user1` login
3. `admin` change the password of  `user1`
4. `user1` can still operate, like change his information

(video)[https://1drv.ms/v/s!AmTWEcd1YDpUjgoJ8lkA8pN8zYEJ?e=gIlbGf]
