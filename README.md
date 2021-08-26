# docker_mongo_express_autoapi
Run MongoDB with Admin UI using mongo express and REST API using auto API

1. Install docker / compose
2. Run
```
docker-compose up
```

- For auth image, the user need to login

#### Authentication

Each API has their own users, so users have to logged specifying the API in the request:

<pre>
<b>POST</b> /login
<b>Content-Type</b>: application/json

{
  "api": "example",
  "email": "user@email.com",
  "password": "pass"
}
</pre>

The response will contain a session token in the headers and body:

<pre>
<b>X-Email</b>: user@email.com
<b>X-Token</b>: 123456

{
  "email": "user@email.com",
  "token": "123456"
}
</pre>

To logout, users have to specify the API too:

<pre>
<b>POST</b> /logout
<b>Content-Type</b>: application/json
<b>X-Email</b>: user@email.com
<b>X-Token</b>: 123456

{"api": "example"}
</pre>
