# docker-lemp SSL

# 📖 Description
Install SSL with let's encrypt on VPS

# ✅ Prerequisites
* Docker-lemp project must be downloaded on your VPS.

# 🚀 Install
1. Rename the install_ssl.conf.example to install_ssl.conf.

2. Add your domain to the file (domain.com).

3. Upload the file to the VPS, on nginx/conf.d (only this file) 

4. Run the containers:
     ```bash
     docker-compose up -d
     ```

5. Run the following command (add all subdomains you want):
      ```bash
      docker-compose run --rm certbot certonly \
      --webroot \
      --webroot-path=/var/www/certbot \
      --email your@email.com \
      --agree-tos \
      --no-eff-email \
      -d domain.com \
      -d www.domain.com \
      -d sub1.domain.com \
      -d sub2.domain.com
     ```

6. Rename the prod.conf.example to prod.conf. Upload it to VPS and remove install_ssl.conf

7. Restart nginx: 
   ```bash
   docker-compose restart nginx
   ```

✅ Now SSL is now running


# 🛠️ Auto renew

Certificate will be valid for 90 days, to renew it automatically, you can add this to cron:
   ```bash
   0 3 * * * docker-compose run --rm certbot renew && docker-compose restart nginx
   ```






