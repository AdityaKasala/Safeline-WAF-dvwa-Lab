# SafeLine WAF + DVWA Home Lab Notes

## Environment Setup
- Ubuntu Server VM configured with bridged networking.
- Installed Apache, PHP, MySQL, git.
- Cloned DVWA repo to `/var/www/html/DVWA`.
- Changed Apache port to 8080.
- Created DVWA database and user with proper permissions.
- Set file permissions for DVWA directory.

## SafeLine WAF Setup
- Installed SafeLine via Docker on Ubuntu Server.
- Registered DVWA app in SafeLine with upstream URL `http://127.0.0.1:8080`.
- SafeLine listens on port 80, proxies requests to Apache's 8080.

## Kali VM Setup
- Kali VM installed and bridged to same network.
- Tested connectivity to Ubuntu Server (some ICMP blocked, HTTP reachable).
- Used Kali’s browser to access DVWA.

## Attack Tests
- Set DVWA security level to low.
- Launched SQL injection payloads: `1' OR '1'='1` in input fields.
- Launched XSS payloads: `<script>alert('XSS')</script>`.
- Observed SafeLine blocking via “Access Forbidden” pages and dashboard statistics.
- Reviewed SafeLine logs for attack details.

## Troubleshooting
- Fixed Docker container names and ensured restarted containers.
- Resolved database user password policy errors.
- Adjusted upstream URL format for SafeLine WAF.
- Cleared browser cache/used incognito mode for UI input issues.
- Resolved network setup issues around bridged adapter in VirtualBox.

## Commands Summary

### Apache & DVWA Setup
sudo apt-get update && sudo apt-get upgrade -y
sudo apt-get install -y apache2 php php-mysql mysql-server git
cd /var/www/html
sudo git clone https://github.com/digininja/DVWA.git
sudo chown -R www-data:www-data DVWA

###Apache port change:
sudo nano /etc/apache2/ports.conf # change Listen 80 to 8080
sudo nano /etc/apache2/sites-available/000-default.conf # change <VirtualHost *:80> to *:8080
sudo systemctl restart apache2

### Database Setup:
CREATE DATABASE dvwa;
CREATE USER 'dvwa_user'@'localhost' IDENTIFIED BY 'p@ssw0rd';
GRANT ALL ON dvwa.* TO 'dvwa_user'@'localhost';
FLUSH PRIVILEGES;

### SafeLine WAF Management
- Check Docker containers:
  sudo docker ps -a
  sudo docker restart safeline-luigi safeline-mgt
- Register application with upstream: `http://127.0.0.1:8080`
- Listen on port 80

### Kali Validation
Check and ping Ubuntu IP:
ip addr show
ping -c 4 192.168.1.215
curl -I http://192.168.1.215:8080/DVWA/

## Attack Payloads Used

| Type          | Payload                  |
|---------------|--------------------------|
| SQL Injection | `1' OR '1'='1`           |
| XSS           | `<script>alert('XSS')</script>` |

---

## Conclusion

Successfully demonstrated SafeLine WAF detecting and blocking web attacks on DVWA in a homelab environment.

---

