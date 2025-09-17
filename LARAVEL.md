# Configurations for laravel

if you upload ```index.php``` in your host and your server has configured, use this eviroment variables in your laravel application.

Example: if your domain is https://storage.domain.com

## Enviroments

```bash
FILESYSTEM_DISK=s3
AWS_ACCESS_KEY_ID=default
AWS_SECRET_ACCESS_KEY=use_any_string_here
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=storage
AWS_URL=https://storage.domain.com
AWS_ENDPOINT=https://domain.com
AWS_USE_PATH_STYLE_ENDPOINT=false
```
