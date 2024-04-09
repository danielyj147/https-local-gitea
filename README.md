# Self-signed HTTPS Local Gitea Server

## Why??

- Why not? 😎

## How to Run

### 1. Generate a Self-signed OpenSSL Certificate

- Run the command below in the project's root directory.
  
```bash
cd <path-to-project-directory>
docker run --rm -v "$(pwd)/certs:/certs" -it alpine/openssl req -x509 -newkey rsa:4096 -keyout /certs/localhost.key -out /certs/localhost.crt -days 365 -nodes -subj "/C=US/ST=YourState/L=YourCity/O=YourOrganization/CN=localhost"
```

*Note: The certificate is only valid for the next 365 days. You **MUST** renew the certificate every 365 days.*

### 2. Write .env

- Create and fill out `.env` file based on `.env.example`

### 3. Run docker-compose.yml file.

- Execute the command below:

```bash
docker compose up -d
```

### 4. Access the Site

- If the server has been set up correctly, you can access the site [here](https://localhost:8003), or at https://YOUR_LOCAL_IP:PORT.

*It has to be https, not http*