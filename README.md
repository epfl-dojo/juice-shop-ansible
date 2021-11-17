# Juice Shop Ansible

This is some Ansible jam to deploy [JuiceShop] and [CTFd].

> ⚠ Beware: this is a work in progress and this is far from perfect or fully automated.


## Goal

The goal is to use Ansible to be able to rapidly deploy some dockers to have an
instance of the [JuiceShop] and an instance of [CTFd] with the JuiceShop
challenges presetted.

The web site [Pwning OWASP Juice Shop] explain different way to do it.


## Pebbles in the shoe

The `bkimminich/juice-shop` docker image is a fast way to deploy the
[JuiceShop], but unfortunably this image doesn't come with the
`juice-shop-ctf-cli` program that we need to generate the challenges for [CTFd].
As a consequence, we have to build our own image based on
`bkimminich/juice-shop`, just for `npm install -g juice-shop-ctf-cli`.

The `ctfd/ctfd` image comes also in a handy way. Almost. First, the
`juice-shop-ctf-cli` export works only with [CTFd] version 2.x, need to
downgrade a lot (current version is 3.4.0, last 2.x is 2.4.3). It would have be
very convenient to be able to setup [CTFd] while installing it (i.e. with
configuration files), but no ways have been found (yet) to setup the default we
want. In addition to this, importing the generated challenges in [CTFd] reset
every configuration you might have previously set. To top it all off, the
`ctfd/ctfd` has not been updated to the latest [CTFd] version (but hey, who
cares, still stuck with the 2.4.3 version). As refered in the [CTFd]'s README,
the correct way would be to use the `docker-compose.yml` provided; it might 
gives more flexibility to configure and set-up [CTFd], but also sounds like a 
lot more work.




[JuiceShop]: https://owasp.org/www-project-juice-shop/
[CTFd]: https://ctfd.io/
[Pwning OWASP Juice Shop]: https://pwning.owasp-juice.shop