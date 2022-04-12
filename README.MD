# Deploy Redash on Rancher
- Edit environment variables in `x-redash-environ`:
  - `REDASH_COOKIE_SECRET`: Random by running the following command:
    ```shell
    python3 -c 'import secrets; print(secrets.token_hex())'
    ```
  - `REDASH_HOST`: Your host name. It will be used when you want to login by OAuth
- Copy content in docker-compose.yaml
- Go to rancher, `Add stack`
- Paste the above content to `docker-compose.yml` input box
- Click create
- Click to service that named `server`, `Execute shell` in its docker container, then run the following command to initialize database tables:
    ```
  /app/bin/docker-entrypoint create_db
  ```
- Now redash is running on service named server and exposing port `5000`
# References
- https://github.com/getredash/setup
- https://redash.io/help/open-source/setup
- https://redash.io/help/user-guide/users/authentication-options