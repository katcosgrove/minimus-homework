# **Minimus Homework**

In the interest of minimizing (lol) the amount of work someone following along at home would have to do, and to accurately demonstrate how I would handle a prompt like this on stage, I have taken some liberties with the assignment prompt.

The URL token is not secured in any way beyond being verified in a separate container from the web content, and nginx expects to receive it as a query parameter. I did stick with docker-compose as a deployment tool, since none of this is production-ready anyway and it minimizes the amount of extra work someone followng along at home would have to do for a similar result.

Since I would expect attendees to mess with this demo on their own at home, I have provided the htpasswd file and self-signed SSL keys. Obviously, I would not publish secrets on github outside of a teaching environment.

## Dependencies

- Docker
- Docker Compose
- this repository

## Use Instructions

Clone this repository and navigate into it:
`git clone https://github.com/katcosgrove/minimus-homework.git && cd minimus-homework`

Build and deploy the containers:
`docker-compose up --build`

Open a browser and attempt the following routes:

1. `http://localhost`

This will redirect from HTTP to HTTPS, and return 403 Forbidden.

2. `https://localhost/test`

This will return 403 Forbidden.

3. `https://localhost/?token=token-bm08jm12`

This will prompt you for a username and password.

`admin | secret-passphrase`

Because you know both the URL token and the login information, nginx will serve you the secret webpage.
