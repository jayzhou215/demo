# 10 billion

### db design
```sql
database name: ten_billion
table name: UserInfo{username, password, email, phone, validToken, valid(bool), createTime, updateTime}
唯一键设计
```

### register
```java
http get: http://www.10billion.com/register?usernmae=xx&password=xx
http post: http://www.10billion.com/register
{
   "username":"xx",
   "password":"xxx",
   ...
}
result: {
    "errno":0, // -1 2 
    "errmsg":xx,
    "data":{
        ".."
    }
}
/** User: username, password, secondPassword, email, phone
* Result: errno, errmsg, data{}
* errno 0, errmsg 请到邮箱中激活
* errno -1, errmsg xxxx
*/
public Result register(User user){
    // valid
    if password != secondPassword:
        return {-1, "password not same"}
    if !validEmail(email)
        return {-1, "invalid email"}
    if email uniq:
        return 
    // sendTokenEmail
    mailto(email, mailmsg)
    saveUser2DB()
}
```

### login
```java
public LoginResult login(User user) {
    // isUserExist
    if (xxx) {
        return {-1, xxx}
    }
    // getUserFromDB
    // checkValid
    return {0, success}
}
```