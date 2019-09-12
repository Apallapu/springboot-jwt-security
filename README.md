# springboot-jwt-security
springboot-jwt-security


steps to develop the springboot-jwt-security application
===========================================================

1.create the username and password by using below uri in application.

http://localhost:9191/register

payload:
==========
{
	"username":"ankamma",
	"password":"ankamma"
}


2.Generating JWT in application
===============================
2.1.client make the request to /autentication endpoint in application

http://localhost:9191/authenticate

payload:
==========
{
	"username":"ankamma",
	"password":"ankamma"
}

2.2. JwtTokemFilter take the request from client and it will check the if request has token or not and then it will call to JwtAuthenticationController class with createAuthenticationToken method.

2.3. Validate the username and password using spring AuthenticationManger of Authenticate method

2.4 Load the user details from data base by passing the username if username is valid it will return true.

2.5. Create jwt token and return back the jwt token in response.


final response:

{
    "token": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhbmthbW1hIiwiZXhwIjoxNTY4MzQxMjM2LCJpYXQiOjE1NjgzMjMyMzZ9.MU7pjEK2_5H_Pt_hiTbvf-6Lx8XAWYocqI435fN6g31yKvfC2yjz8NlbVHMN523vQ18UF9_O6RQwKu311eBEkg"
}


Validating JWT
===============
3.1 client make request with below uri with token in header

http://localhost:9191/hello

eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhbmthbW1hIiwiZXhwIjoxNTY4MzM5MzY5LCJpYXQiOjE1NjgzMjEzNjl9.bYPqne7HG4e8zfs_O-g8k2o-3peOocoLESpuaZxl6XIFr9z_DLkjxlNOjoQk_lb4BN_2Zv7TFvriYv2vcO2_8w


3.2. if request has token,if yes extract the token .

3.3. load the user details from database by passing the username

3.4 validate the token if the token is valid then call to /hello api

response:
======
Hello World





