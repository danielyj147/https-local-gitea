# Self-signed Https Local Gitea Server 

## How to Run

### 1. Get Self-signed OpenSSL Credential

- Run the cmd below at the project root directory.
  
```bash
cd <path-to-project-directory>
docker run --rm -v "$(pwd)/certs:/certs" -it alpine/openssl req -x509 -newkey rsa:4096 -keyout /certs/localhost.key -out /certs/localhost.crt -days 365 -nodes -subj "/C=US/ST=YourState/L=YourCity/O=YourOrganization/CN=localhost"
```

*Notice that the certification is only valid for the next 365 days. You **NEED** to renew the certification every 365 days*

### 2. Write .env

- Create & fill out `.env` file based on `.env.example`

### 3. Run docker-compose.yml file.

- Run the cmd below.

```bash
docker compose up -d
```

### 4. Access the Site

- If the server was set up correctly, you can access the site at https://SERVER_NAME:PORT

*It has to be https, not http*