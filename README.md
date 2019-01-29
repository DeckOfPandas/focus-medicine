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

Run configuration wizard:
* Mostly as you'd expect
* GitHub repo must be initialized before adding
* Add SSH key from new box to GitHub


### Gotchas

* Permissions for id_rsa files must be correct, i.e. sensible
* Don't add the port to the end of the base url
* After wizard has finished, nginx error 502 --> `sudo node wiki start` by hand, as doesn't work without sudo??? Something to do with pm2???
 ```
⠙ Setup wizard terminated. Restarting in normal mode...(node:16898) UnhandledPromiseRejectionWarning: Error: Command failed: node wiki start
events.js:183
      throw er; // Unhandled 'error' event
      ^

Error: connect EACCES /home/helen/.pm2/rpc.sock
    at PipeConnectWrap.afterConnect [as oncomplete] (net.js:1191:14)


    at Promise.all.then.arr (/var/www/wikijs/node_modules/execa/index.js:236:11)
    at <anonymous>
    at process._tickCallback (internal/process/next_tick.js:189:7)
(node:16898) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 2)
(node:16898) [DEP0018] DeprecationWarning: Unhandled promise rejections are deprecated. In the future, promise rejections that are not handled will terminate the Node.js process with a non-zero exit code.
```
