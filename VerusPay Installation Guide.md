## VerusPay Installation guide for WooCommerce

:warning: Disclaimer no SSL secuirty and IP locking of the firewall is mentioned in this guide, PLease use at your own risk.  Add S


This guide will show you how to setup the VerusPay plugin so that your WooCommerce store can accept cryptocurrency payments from VRSC, KMD, ARRR, ZCASH & more. 

What is covered
: ***How to install WordPress on a server***, which gives you a website for people to visit.  With the this website you can create blog pages, news pages, idea pages, anything your creative mind desires, but most importantly your WordPress site allows you to run an online shop using a Plug-in called WooCommerce.

: ***How to install the VerusPay Plugin in WooCommerce***, armed with a running WordPress Website, next step is to setup the VerusPay Plugin that gives the customer the option to choose VRSC, KMD, ARRR, ZCASH & more cryptocurrencies as payment options. 

: ***How to install the Verus Command Line Wallet***, you'll need an interface to the Verus block-chain to send and receive money to anyone in the whole world.  With this unassuming text based program running on your server computer, it allows you to receive payments from customers and send them to your own personal wallet or wherever you want to process them.  It also enables you mine and stake your cryptocurrency if you so choose.

: ***How to install Verus ChainTools***, having a shop and a wallet enables you to to process customers orders and handle cryptocurrency, but we need to connect them together so that the shop website can request payment information from your wallet.  This is where ChainTools comes in, it keeps your cryptocurrency wallet  separate from your website traffic for safety.  It also allows you to connect to multiple Command line wallets to your shop so you can accept more than one type of cryptocurrency.

: ***How to test that you have successfully set everything up***, to confirm everything went well and that your shops up and running we'll guide you through all the checks and tests you need to do. 

## Things you'll need
Okay, so you've got a killer new product and you want to get it into your own online shop.  You could dig out that old laptop you have had for years lying in the draw and have everything running on that.   However this is highly not recommended due to speed, scalability, down time, backup all the things we know and love about websites.

What you'll need
- A server 
	- This is computer that is permanently running in a data centre somewhere.  It has a fast internet connection to allow hundreds of people to connect to it. It is probably is battery backed up, and has lots of space available. Designed for website hosting.
	- There is a plethora of server providers out there that can provide you with a computer you can rent.  This guide will use [DigitalOcean](http://cloud.digitalocean.com). However there are many others available.
	- The specification of the server if you intend to run one shop and one cryptocurrency payment method must be a minimum of 4GB of RAM, 25GB of hard drive space, and two CPU cores are recommended.
	- The server will have an operating system on it and unfortunately windows is out, so we will use a free operating system called Linux.  The flavour of Linux called Ubuntu 18.04 LTS.
- A home computer to do all the setup and management on.
	- This can be Windows or Ubuntu machine
	- You will need a way of talking to the Linux server, this guide will use a program called [MobaXterm](https://mobaxterm.mobatek.net/download-home-edition.html). Its like a remote control to the server.
- Links to all the free software that you will need to download
	- [VerusCoin Github](https://github.com/VerusCoin) A repository of all the Verus related software and tools you'll need
	- [Verus Wiki](https://bootstrap.veruscoin.io/) A wealth of How-to guides for Verus
	- [VerusPay](https://github.com/monkins1010/VerusPay) & [ChainTools](https://github.com/monkins1010/ChainTools) - Currently the most up to date software to use.

## Getting Started
#### Setting up your WordPress Website
1. Goto [Digital Ocean](https://cloud.digitalocean.com/) and setup an account, this [Referal Link](https://m.do.co/c/cf6b23e11b50) will  get you $100 to spend over 60 days. After that the Plan we are loooking at is around $20 a month at time of writing June 19th 2020.
2. Create a Droplet (this is what Digital ocean call servers).

Go to   
![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/droplets.png)
 on the left hand panel in the Digital Ocean website.

---
At the top select  
	![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/createdroplet.png)

---

Then Pick `Marketplace`  >> `WordPress on 18.04`

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/ocean_chooseanimagewordp.png)

---

Choose from the Standard Plan the 4GB RAM, 2 CPU Cores, 80GB HD Space for $20 a month.

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/ocean_20dollaplan.png)

---

Choose your region you want the server to reside, think of your customers location and if they are all American citizens then pick  one in that region.
![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/ocean_chooseregion.png)

---

Next skip down to `Authentication` ,we are going to log into the server with a special key (SSH Key) which is an encrypted password that will be stored on your computer.  This is a very strong password and means that only you will be able to log onto the server.

Below you can see that I have already created two keys one called `laptop` & `i7` these are two different computers.  So they will both be able to log onto the server if we select them both.  To create a new one.  Click  `New SSH Key`

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/ocean_newsshkey.png)

This will pop up with a window in which you need to paste your SSH Key into.  But before we do that you need to install and load up Mobaxterm (Or your other favourite SSH Terminal).  

---

Install Mobaxterm by downloading the free  [MobaXterm Home Edition v20.2 (Installer Edtion)](https://mobaxterm.mobatek.net/download-home-edition.html)
Click the `MobaXterm Home Edition v20.2 (Installer Edtion)` Green button int he website above and download the zip file.  Once the zip file is down loaded, double click it and run the installer program inside it called `MobaXterm_installer_20.2.msi`

Once Installed you will get a new icon on your desktop called `MobaXterm`. Double click it and load it up, you will be greated with a blank page, click the `Start local terminal` below.

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/moba_start_local_terminal.png)
This will bring up a black Terminal window where you will be doing most of setting up of your website.

---
In the local terminal we need to make a local SSH key so type in `ssh-keygen` and press enter.
![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/moba_create_pubkey_pair.png)

Enter the file name `verus` then press enter.

:warning:You can add a passphrase (password) if you want extra security, otherwise if you are a home computer that only you will use you can leave it blank.  If you choose a passphrase e.g. `Kettleteapotegg129!"#` Make sure you **Write it down somewhere safe** as you'll need it every time you log on to the server.:warning:

---

Once you have finished this there will be two files made in your `This PC > Documents > MobaXterm >home > .shh`  directory.   Open the file called `verus.pub` in note pad by `Right-clicking on the file`  and choose `Open with`
![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/windows_openverus_pub_with.png =500x300)

---

Then Choose `notepad`  and click `OK` at the bottom.

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/windows_open_with_notepad.png =400x500)

---

Once the verus.pub file is open, select all the contents inside it by pressing `ctrl + a` then copy it.

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/windows_copy_pubkey_for_ocean.png)

---

Then go back to your web browser on the digital ocean site and paste it into `SSH key content` call the key a name that references your computer like `Main_desktop_computer_Bill` then click add.

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/ocean_paste_in_key.png =380x300)

Now you have your SSH Public Key on digital ocean it will load that into your server when you create it so that only you can access it.

Next Select the keys that you want to associate with your website, by click the square checkbox next to your friendly name you chose.  Then you can skip down to `Create Droplet` at the bottom.

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/ocean_create_droplet.png)

---

The website will take a couple of minutes to create the website, once its done you will see an IP address in the 



![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/ocean_your_ip.png)

Now your WordPress site is setup and ready to configure on the internet

---
#### Setting up an Admin user on WordPress to get the security set

As soon as the droplet is created your website will be available on the internet at  http://<<your_ip_of_your_droplet>>

You will be greeted with a website asking you for your language, choose you language then fill in the form below 
:warning: pick a strong passord and write it down :warning:

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/2/wordpress_firstdetails.png)

Once you have filled in the form, you will then be asked to login.  Login with your chosen Username and password and you;ll be greated with this screen:

Go to `Plugins` and install `WooCommerce`

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/2/wordpress_first_mainscreen.png)

Click the search box and find the WooCommerce plugin, then click install.

Next To install the Verus pay Plugin download this file to your desktop:
https://github.com/monkins1010/VerusPay/archive/master.zip

To install this zip goto `Add new` in plugins then go to `Upload Plugin`


![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/2/wordpress_choose_plugin.png)

Choose the zip you just downloaded to your desktop called `VerusPay-master.zip`
 
---
Once complete you will see a message saying `Plugin installed succesfully`


![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/2/wordpress_verus_installed.png)

---
# Setting up the Wallet

#### Logging into your server with MobaXterm for the first time

Back at MobaXterm create a new session by clicking in the white space shown below and choosing `New session`


![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/moba_new_session.png)

---

Next select `SSH`  and enter you IP address from the digital ocean site.  Specify the user `root` and Port `22` .  

Select the `Advanced SSH settings` 

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/moba_setup_session.png)


---
Select `Use private key`  and find the `verus` file from `This PC > Documents > MobaXterm >home > .shh`  directory. 



![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/moba_choose_verus_pub.png)

---

Next input a Friendly name for the Session `Wordpress root` is suitable.  You wont use this account all the time because we'll make another account later..



![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/moba_setname.png)

---
Now you can double click on the newly created WordPress user and you should get a connection to your server and window like this:


![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/2/wordpress_firstlaunch.png)

We can skip this step and worry about giving you site a nice name like `www.brians_laptops.com` later... i.e. a domain name and not just the four set of numbers we are typing into the web browser at the moment. So press `CTRL + C` to quit out and get to a new line called `root@wordpress-s-2vcpu-4gb-nyc1-01:~#`

---

#### Setup Verus Command Line Wallet

Create a new user that we will log in as to install the Verus Command line wallet.

type in `adduser wallet` then press enter.
:warning: Set a password, this will be used when the wallet user wants to do something that requires extra privileges **Write it down as wallet password** :warning:
Press enter for all the user names and accept the default

Type: (To make the wallet a sudo user)

`usermod -aG sudo wallet`

`mkdir /home/wallet/.ssh`

Make the directory only executable by the user:

`chmod 700 /home/wallet/.ssh`

Copy the  `authorized_keys`  file that contains your public key:

`sudo cp /root/.ssh/authorized_keys /home/wallet/.ssh/authorized_keys`

Make everything in  `.ssh`  owned by your user:

`sudo chown -R wallet:wallet /home/wallet/.ssh`

Make it readable only by your user:

`sudo chmod 600 /home/wallet/.ssh/authorized_keys`

Now there is a new user called wallet who we can log in as.. to do this we can duplicate outr current session in MobaXterm.

Right click on the session name you created earlier in the MobaXterm left hand window.  If you cant see it click on the little house icon at the top

#### Logging in as wallet
Right click on the Verus Root session in MobaXterm and select `Duplicate session`.

You will have a new session called Verus root (2), right click on this and `edit session` then change the name in `specifiy username` from `root` to `wallet`.   Also change the name of the session by going into `Bookmark settings` and changing the session name from `Verus root(2)` to `Verus wallet` 

Now double click on your new `Verus wallet` session and you should be greeted with this:
![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/3/moba_wallet_loggedin.png)

#### Downloading the Verus Command Line Wallet and installing it

First we need to update linux so run

`sudo apt-get update`   type in your wallet password  from earlier when prompted.

Then type in

`sudo apt-get install build-essential pkg-config libc6-dev m4 g++-multilib autoconf libtool ncurses-dev unzip git python python-zmq zlib1g-dev wget libcurl4-openssl-dev bsdmainutils automake curl`

Press `Y` to continue when asked.

Go to:
[https://github.com/VerusCoin/VerusCoin/releases](https://github.com/VerusCoin/VerusCoin/releases/latest)

Pick the latest release. and find the Verus-CLI-Linux-v0.7.0-3-amd64.tgz  at the bottom,
at the current time of writing. right click on it and `copy link address`

type `wget` wallet session followed by a space then right click in the terminal window to paste in the command.

It should say:

`wget https://github.com/VerusCoin/VerusCoin/releases/download/v0.7.0-3/Verus-CLI-Linux-v0.7.0-3-amd64.tgz` 

`tar -xvf Verus-CLI-Linux-v0.7.0-3-amd64.tgz`

`tar -xvf Verus-CLI-Linux-v0.7.0-3-amd64.tar.gz`

now in /wallet/verus-cli the wallet is installed

`cd verus-cli`

`./fetchparams`  This will download a load of files should take about 3 minutes on Digital Ocean.

Once complete

`cd`

`mkdir -p .komodo/VRSC`

`cd ~/.komodo/VRSC`

Download the block-chain bootstrap, this considerably speeds up synchronisation of the block-chain from days to minutes...

`wget https://bootstrap.veruscoin.io/VRSC-bootstrap.tar.gz`

`tar -xvf VRSC-bootstrap.tar.gz`

`cd ~/verus-cli`

Now you can fire up the Wallet and get it to synchronise with the block-chain.

`screen -S verus ./verusd`

`ctrl +a` then `ctrl +d` to get back to the terminal and leave the Wallet running in a `screen`

## Installing ChainTools

We need to install the ChainTools on the webserver so we can remotely run the setup.
`cd`  To get back to the wallet directory.

`git clone https://github.com/monkins1010/ChainTools.git `

This will make a folder called `~/ChainTools` with a mini server in that acts a go between from the Shop to the wallet.

`sudo cp -ar ~/ChainTools /var/www/html` Put the ChainTools folder in your website.

`sudo chown -R www-data:www-data /var/www/html/ChainTools`

Go to http://<yourwebsiteip>/ChainTools/ in your web browser.

You'll see "Welcome to the VerusChainTools Installer"
![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/3/chain_spash.png)

copy down your private access code and update code and put it in a document somewhere safe on your computer preferably in a pass-worded file.

Choose VerusPay Wordpress mode

:warning::warning::warning:Important!!!!!!!! If you are selecting VRSC Type in **VRSC** even though its there:warning::warning::warning:

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/3/chain_must_type_in_VRSC.png)

Then click `Add chain`

---
Type in a name and the VRSC wallet location as below
![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/3/chain_put_in_addresses.png)


Fill in the payout address you want he shop to pay to.. e.g. you home personal VRSC addresses/

Press `Save`

The Website should change to `Successfully Installed!`

Need to firewall ChainTools folder so no access allowed by external see guide


## Final setup and test

Back to your browser type in the http://<<your_ip_of_your_droplet>>

Goto plugins and activate the WooCommerce plugin.  Follow through the wizard to get your basic shop ready. (it can be changed after)

Then go back to Plugins and choose `Activate` on the VerusPay plugin.

Then click `Configure` Below the VerusPay plugin.

Scroll down to this screen and type in the info as shown. replace the IP with `127.0.0.1/ChainTools/`.  Then click continue.
![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/3/chain_connection_params.png)

Put in your access code from setting up the ChainTools then press `Save`

---
Next go back into he `configure` in the `VerusPay` Plugin.

First we need to check its connected to the wallet you should see a `Online` in green if everything is happy.

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/3/plugin_enable_Verus_payments.png)

To turn the wallet on first goto Options and set the firs 5 values to something, as below

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/3/chain_options_plugin.png)

---
Then go to `Wallets` back in the Veruspay plugin and first turn on 

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/3/plugin_enable_Verus_payments_small.png)

Then Press save at the bottom.

---

Then go to the Daemons Tab and select Enable Verus.  It has to be done in this order :warning:
![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/3/plugin_enable_veruspay.png)

![Alt](https://github.com/monkins1010/Verusguideassets/raw/master/moba_setname.png)

Congratulations your shop is now set up to accept VerusPay.

Thankyou

Chris - Monkins1010

## Further Considerations

* There is no fallover set so if the wallet goes off line people cannot payments.  Please see the **adding 500 addresses incase of wallet discconection**
* Security should be a lot firmer than this guide, it is just a setup guide to show the steps, further action must be taken to:
	* Encrypt the traffic from the website i.e. use SSL 
	* Firewall the wallet and the Chaintools.php files more securely.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjIwNTg0ODgzLC05NjA4NjIyNjgsNTg5Mz
I3MDM3LDIwNDI3NTUwMzksLTYxODg2Mzk1NywtNTUyMzM4NzY4
LDEyNDg3NzQwNDgsLTI4MDkyNTEyOCwtMTc0NDkyNzQ4MywxNz
gwMzM2MzUsMjA0NjIwNTAzMiwtMTUyMzM2NTk3NywxOTIwNjkx
MDQ3XX0=
-->