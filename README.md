## About

This is a quick bash script I wrote to automate creating user hosting accounts on CentOS. It's probably too specific to cater for your needs, I've put it on GitHub so I can manage the code deployed to my servers and there's no harm in sharing it.

You can change paths to reflect your system, but, it's written to work with the following assumptions.

* PHP5.3 or PHP5.2 in PHP-FPM mode. It expects you front the FastCGI handler with Nginx. 
* It expects your run a single Nginx instance with per-user PHP-FPM listeners.
* It expects you create a single Nginx configuration for each server VHOST and use a symbolic link to enable/disable
* It expects you create a single PHP-FPM configuration per listener
* It expects you create a new user for each 'account' and that user is used to run the PHP-FPM listener
* It expects you use VSFTPD with an authorised users configuration using 'user_list' and 'chroot_list'
* It expects you use chkconfig to enable and disable your PHP-FPM listeners
* It expects you to have a skeleton directory available containing your default hosting account structure.

## Dependencies

Aside from the assumptions above, this script relies on mkpasswd which is available in yum in the 'expect' package

## Usage

createUser example.com [php53 || php52]

example.com will be created as a web-root, the account name, and used as part of the filename for all the configuration files created. On my systems both PHP52 and PHP53 are availabe and this script will allow you to specify what type of account is to be created, in simple terms depending on which you select determins which template files are used.