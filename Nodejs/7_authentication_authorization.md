#


### authentication:

- Vefies the identify of the user.


eg: Login using email and password


### Authorization:
- Determine authenticated user is allowed to access.

eg: Admin user has privileges of manage users.


### JWT:
- JSON web Token. Used to transfer signed claims between parties
- Consist of three parts:
    - Header.
    - Payload.
    - Signature.

header.payload.signature




```javascript

const jwt=require('jsonwebtoken');

const token=jwt.sign(
  {
    userId:5,
    role:"admin"
  },
  process.env.SECRET_KEY,
  {
    expiresIn: '1h'
  }
);


const decoded=jwt.verify(
  token,
  process.env.SECRET_KEY
);


console.log(decoded);


```

### JWT Authentication Works:

1. User enter login credentials.
2. Backend validate the credentials.
3. Backend creates the JWT with details.
4. Client send the token for every request.


### diff between access token and refresh token:

| Access token | Refresh Token |
| ------- | ------------- |
| Used to access APIs | used to create the access token |
| short lived | Long Lived |
| Limits exposure duration | Must be protected safely |

### What is Bcrypt:
- Password hashing Library used to secure the password.

```javascript

const bcrypt=require("bcrypt");

const hashedPassword=await bcrypt.hash(bcrypt,12);

const isValid=await bcrypt.compare(enteredPassword,hashedPassword);

```

### RBAC:
 - Role Based Access Control.
 - controls the access based on roles.


 ```javascript

function authorize(...roles){
  return (req,res,next)=>{
      if(!roles.includes(req.user.roles)){
        return res.status(403).json({
          message: "User doesnot have the access"
        })
      }
  }
}

app.get('/admin',authenticate,authorize(SUPER_ADMIN,STAFF),getAdmin);

```

### Diff between 401 and 403:

- 401 - Request lacks the authentication.
- 403 - Server understands the request but refuses authorization.

### Password Salting:
- add the random value(salt) before the hashing.

```javascript
const salt=await bcrypt.salt(10);

bcrypt.hash(password,salt);
```

### Multi Tenant Architecture:
 - Multiple organisation or customer to use the same application.
- eg: civitech

 User.findAll({
    client_id:req.client_id,
    is_deleted:false
 })

 