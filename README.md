# Centos7 nginx

Vagrant file has provisioning, but the box itself is from the URL below

```
vagrant box add centos7 https://github.com/tommy-muehle/puppet-vagrant-boxes/releases/download/1.1.0/centos-7.0-x86_64.box
vagrant init centos7
vagrant up
```

## Then do

- Have a service you know running somewhere at http://<ip>:<port>/<endpoint>
- Modify the `express.conf` file to refer to the ip/port of your service
- Copy `express.conf` to the Vagrant box at `/etc/nginx/conf.d/express.conf`
- Remove the `server` block from `/etc/nginx/nginx.conf`

## Observe

If everything is tied together correctly, this should work

- `curl -X GET http:<vagrantboxip>/api`

as nginx should forward that request on according to the  `location#proxy_pass` rule in `express.conf`
