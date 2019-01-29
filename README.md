# focusmedicine.com

## Helen's setup notes

### Docs used

  * https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04
  * https://wiki.js.org/get-started.html
  * https://websiteforstudents.com/install-wiki-js-on-ubuntu-16-04-17-10-18-04/  

Make a box:  
1. Create new DigitalOcean droplet on Ubuntu 16.04
  * Min 1GB memory, >=2GB strongly recommended
2. Set up server as per: 
  * Users  
  * RSA keys  
  * Simple firewall  

Install things:  
1. Install Node.js  
  * curl from nodesource    
  * install via apt  
2. Install MongoDB  
  * Via apt  
3. Download and install Wiki.js  
  * Create `/var/www/wikijs`  
  * Download via curl  
4. Configure Wiki.js using wizard  
  * `sudo node wiki configure 8192`  
  * Port 8192 for now  
