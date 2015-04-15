The Nginx Vhost project exists to provide a simple shell script to generate a vhost directory.
This project is built on/for Ubuntu servers, and will likely not work on other platforms.

For best results, we recommend:
Ubuntu 10.10 (Maverick)

Depends:
ack-grep

Expects that user www-data exists.
Expects script to be executed by a user that can su to www-data.
Expects Nginx to already be installed, and expects user to restart Nginx when the vhost is ready.

Bottom of /etc/nginx/nginx.conf "http {" block should have a line like the following:
    include /var/www/*/conf/nginx.conf;


Example usage as root user:
# cd /var/www/
# git clone https://github.com/kvasilov48/nginx-vhost/
# nano -w nginx-vhost/generate_vhost # To change VHOSTDIR & VHOSTSKEL as necessary
# chmod +x nginx-vhost/generate_vhost # Make the script executable
# /var/www/nginx-vhost/generate_vhost # Execute the script, follow prompts to TYPE IN the domain and TYPE IN the IP


Example domain: test.mysite.com
Example IP (typed in from list provided): 222.222.222.222

Files are then copied into /var/www/ (VHOSTDIR) as /var/www/test.mysite.com/
That directory contains:
backup/
conf/     # Per-domain nginx config is stored here
public/
private/
log/
