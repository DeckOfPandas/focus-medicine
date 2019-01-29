# focusmedicine.com

## Helen's setup notes

### Docs used
  * https://wiki.js.org/get-started.html (not that useful tbh)
  * https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04
  * https://www.vultr.com/docs/how-to-install-wiki-js-on-ubuntu-18-04

### Step by step

Make a box:  
* Create new DigitalOcean droplet on Ubuntu 16.04
  * Min 1GB memory, >=2GB strongly recommended
* Set up server as per https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04
  * New user with sudo
  * Timezone
  * RSA access  
  * Simple firewall  

Install things:
* Quick overview: https://www.vultr.com/docs/how-to-install-wiki-js-on-ubuntu-18-04
* Install Git (v2.7.4 here)
* Install Node.js (v10.x here)
* Install MongoDB (v3.2 here)
* Put a standard web server in front -- nginx as per https://www.vultr.com/docs/how-to-install-wiki-js-on-ubuntu-18-04
* Configure nginx
* Install Acme.sh client and get a LE certificate
* Download and install Wiki.js inside /var/www/wikijs
* Run server and configure using wizard
  * `node wiki configure`  
  * Default port is 3000, need to change in nginx proxy settings if altered
* Install PM2 and set up as startup service

### Configuration wizard
* System check likes our settings so far: [image]
