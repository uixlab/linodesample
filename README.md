# linode-guide-sample
Outline for a guide on How to build and configure Nginx with Naxsi from source on Ubuntu 16.04.




### Outline for a guide on How to build and configure Nginx with Naxsi from source on Ubuntu 16.04.
#### Steps 
- introduction
- before you begin
- downloading the source code 
- prepare Nginx for building
- compile the nginx with naxsi on your Linux kernel
- create a systemd service to control nginx
- configure and secure nginx with naxsi

# How to build and configure Nginx with Naxsi from source on Ubuntu 16.04.
## Introduction

NGINX is a free, open-source, high-performance HTTP server and reverse proxy, as well as an IMAP/POP3 proxy server. NGINX is known for its high performance, stability, rich feature set, simple configuration, and low resource consumption.
It is quite modular by design. It has native modules and third-party modules created by the community. Written in the C programming language, it's a very fast and lightweight piece of software.

One of these modules is Naxsi which is by itself a third party Nginx module, available as a package for many UNIX-like platforms. It  provides web application firewall features. It brings additional security to your web server and protects you from various web attacks such as XSS and SQL injections.

This tutorial shows you how to build and configure Nginx with Naxsi from source.

## Before You Begin

Before following this tutorial, please make sure you complete the following prerequisites:

-  You should not have a pre-existing installation of NGINX. If you do, back up the configuration files if you want to retain their information, and then purge NGINX.

-  You will need root access to the system, or a user account with `sudo` privileges.

-  Set your system's [hostname](/docs/getting-started/#setting-the-hostname).

-  Update your system's packages.

Except otherwise noted, all of the commands that require root privileges in this tutorial should be run as a non-root user with sudo privileges.

## Downloading the source code

We are going to use nginx-1.9.9 and naxsi-0.56rc1. To install it from source, we need to fetch both nginx and naxsi sources.

Download Nginx's and Naxsi's source code and extract them:


wget http://nginx.org/download/nginx-1.9.9.tar.gz && tar xzvf nginx-1.9.9.tar.gz
wget https://github.com/nbs-system/naxsi/archive/0.56rc1.tar.gz && tar xzvf 0.56rc1.tar.gz

##  Prepare Nginx for building

#### Requirements for building Nginx from source
Mandatory requirements:
- `OpenSSL` library
- `Zlib` library
- `PCRE` library
- `GCC` Compiler

Nginx is a program written in C, so we need to install the C compiler (GCC)


sudo apt install build-essential -y

Download the Nginx dependencies' source code and extract them:


wget https://ftp.pcre.org/pub/pcre/pcre2-10.31.tar.gz && tar xzvf pcre2-10.31.tar.gz
wget http://www.zlib.net/zlib-1.2.11.tar.gz && tar xzvf zlib-1.2.11.tar.gz
wget https://www.openssl.org/source/openssl-1.1.1-pre2.tar.gz && tar xzvf openssl-1.1.1-pre2.tar.gz


Remove all .tar.gz files. We don't need them anymore:

command
rm -rf *.tar.gz
Remove old nginx files and move the naxsi directory


rm -rf /usr/local/nginx
mkdir /usr/local/nginx/
mv naxsi-0.56rc1/ /usr/local/naxsi-0.56rc1/


Remove all downloaded files from the home directory, in this case `/home/username`:
cd ~
rm -r nginx-1.9.9/ openssl-1.1.1-pre2/ pcre2-10.31/ zlib-1.2.11/

##  Compile the nginx on your linux kernel
For help, you can list available configuration switches by running:

./configure --help

Configure, compile, and install NGINX:



## ....more steps remaining
