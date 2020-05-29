# Ansible DOA Module 3 Playbook
Written for use in the Ansible DOA Module 3 CI pipeline.  Can be used standalone.

# NGINX configuration change LAB

```
server {
    listen 443 ssl;
    server_name ~^DOA_Labs_Module3_FOSS_Java_Manual_CI\.*;

    ssl_certificate /etc/nginx/ssl/{{ domain_name }}.pem;
    ssl_certificate_key /etc/nginx/ssl/{{ domain_name }}.key;

    access_log  /var/log/nginx/access.log logstash;

    auth_ldap "Forbidden";
    auth_ldap_servers mdop;

    proxy_set_header host $host;

    location /petclinic {
      proxy_pass  http://DOA_Labs_Module3_FOSS_Java_Manual_CI:8080/petclinic;
      proxy_http_version 1.1;
      proxy_set_header Upgrade $http_upgrade;
      proxy_set_header Connection "upgrade";
      proxy_set_header Host $host;
    }
}
```

# License
Please view [license information](LICENSE.md) for the software contained on this image.

## Documentation
Documentation will be captured within this README.md and this repository's Wiki.

## Issues
If you have any problems with or questions about this image, please contact us through a [GitHub issue](https://github.com/majidpal/mdop-cartridge-ansible-demo-scenario-playbook/issues).

## Contribute
You are invited to contribute new features, fixes, or updates, large or small; we are always thrilled to receive pull requests, and do our best to process them as fast as we can.

Before you start to code, we recommend discussing your plans through a [GitHub issue](https://github.com/majidpal/mdop-cartridge-ansible-demo-scenario-playbook/issues), especially for more ambitious contributions. This gives other contributors a chance to point you in the right direction, give you feedback on your design, and help you find out if someone else is working on the same thing.
