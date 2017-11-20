# Links to stuff that doesn't fint elsewhere

* [Pandoc 2 PDF](http://www.mscharhag.com/software-development/pandoc-markdown-to-pdf)
* [an-introduction-to-serenity-bdd-with-cucumber](http://thucydides.info/docs/articles/an-introduction-to-serenity-bdd-with-cucumber.html)
* [JBehave Getting started](http://jbehave.org/reference/latest/getting-started.html)
* [Selenium, Cucumber Java]](https://github.com/selenium-cucumber/selenium-cucumber-java/blob/master/doc/canned_steps.md#assertion-steps)
* [Selenium Cucumber, Java - Volker](https://github.com/volkerbenders/selenium-cucumber-java)
* [MAC Lookup, Passwords, Geeky stuff](http://wintelguy.com/index.pl)
## String Replace w `sed`

### Replace everything

This example replaces all occurences of 'ORM' with 'ORM w JPA' in `orm_en.html`
Simple and easy - No Headache.

```bash
sed -ie 's/ORM/ORM w JPA/g' orm_en.html
```

## SSH

### Copy RSA-ID to remote host

Passwordless login makes use of public keys and is really neat.
But one hurdle: you've to transfer the public part of the public-/private keypair to the remote host.
The private counter part is yours - and yours alone. Dont share it - dont even post it on facebook ;-)
On some system there`s a command called `ssh-copy-id` do perform the transfer. How about the absence of this tool?
You can use the following bash command - requires you to enter the password for the last time:

```bash
cat ~/.ssh/id_rsa.pub \
  | ssh user@123.45.56.78 \
  "mkdir -p ~/.ssh && cat >>  ~/.ssh/authorized_keys"
```
## ImageMagick

### Watermaks
* [Easy Watermarking](http://www.linuxjournal.com/content/easy-watermarking-imagemagick)

## MQTT
- [Cattle Crew Mosquitto & Docker](https://thecattlecrew.net/2017/02/24/a-tiny-mqtt-broker-docker-image/)
- [Eclipse Mosquitto on Docker](https://hub.docker.com/_/eclipse-mosquitto/)
- [GoodToKnow DB - FuseBits](http://www.gtkdb.de/index_18_1044.html)
- [Meteor, Heroku, MongoDB](https://www.coshx.com/blog/2016/08/19/how-to-deploy-a-meteor-1-4-app-to-heroku/)
