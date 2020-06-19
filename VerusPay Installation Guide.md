---


---

<h2 id="veruspay-installation-guide-for-woocommerce">VerusPay Installation guide for WooCommerce</h2>
<p>This guide will show you how to setup the VerusPay plugin so that your WooCommerce store can accept cryptocurrency payments from VRSC, KMD, ARRR, ZCASH &amp; more.</p>
<dl>
<dt>What is covered</dt>
<dd>
<p><em><strong>How to install WordPress on a server</strong></em>, which gives you a website for people to visit.  With the this website you can create blog pages, news pages, idea pages, anything your creative mind desires, but most importantly your WordPress site allows you to run an online shop using a Plug-in called WooCommerce.</p>
</dd>
<dd>
<p><em><strong>How to install the VerusPay Plugin in WooCommerce</strong></em>, armed with a running WordPress Website, next step is to setup the VerusPay Plugin that gives the customer the option to choose VRSC, KMD, ARRR, ZCASH &amp; more cryptocurrencies as payment options.</p>
</dd>
<dd>
<p><em><strong>How to install the Verus Command Line Wallet</strong></em>, you’ll need an interface to the Verus block-chain to send and receive money to anyone in the whole world.  With this unassuming text based program running on your server computer, it allows you to receive payments from customers and send them to your own personal wallet or wherever you want to process them.  It also enables you mine and stake your cryptocurrency if you so choose.</p>
</dd>
<dd>
<p><em><strong>How to install Verus ChainTools</strong></em>, having a shop and a wallet enables you to to process customers orders and handle cryptocurrency, but we need to connect them together so that the shop website can request payment information from your wallet.  This is where ChainTools comes in, it keeps your cryptocurrency wallet  separate from your website traffic for safety.  It also allows you to connect to multiple Command line wallets to your shop so you can accept more than one type of cryptocurrency.</p>
</dd>
<dd>
<p><em><strong>How to test that you have successfully set everything up</strong></em>, to confirm everything went well and that your shops up and running we’ll guide you through all the checks and tests you need to do.</p>
</dd>
</dl>
<h2 id="things-youll-need">Things you’ll need</h2>
<p>Okay, so you’ve got a killer new product and you want to get it into your own online shop.  You could dig out that old laptop you have had for years lying in the draw and have everything running on that.   However this is highly not recommended due to speed, scalability, down time, backup all the things we know and love about websites.</p>
<p>What you’ll need</p>
<ul>
<li>A server
<ul>
<li>This is computer that is permanently running in a data centre somewhere.  It has a fast internet connection to allow hundreds of people to connect to it. It is probably is battery backed up, and has lots of space available. Designed for website hosting.</li>
<li>There is a plethora of server providers out there that can provide you with a computer you can rent.  This guide will use <a href="http://cloud.digitalocean.com">DigitalOcean</a>. However there are many others available.</li>
<li>The specification of the server if you intend to run one shop and one cryptocurrency payment method must be a minimum of 4GB of RAM, 25GB of hard drive space, and two CPU cores are recommended.</li>
<li>The server will have an operating system on it and unfortunately windows is out, so we will use a free operating system called Linux.  The flavour of Linux called Ubuntu 18.04 LTS.</li>
</ul>
</li>
<li>A home computer to do all the setup and management on.
<ul>
<li>This can be Windows or Ubuntu machine</li>
<li>You will need a way of talking to the Linux server, this guide will use a program called <a href="https://mobaxterm.mobatek.net/download-home-edition.html">MobaXterm</a>. Its like a remote control to the server.</li>
</ul>
</li>
<li>Links to all the free software that you will need to download
<ul>
<li><a href="https://github.com/VerusCoin">VerusCoin Github</a> A repository of all the Verus related software and tools you’ll need</li>
<li><a href="https://bootstrap.veruscoin.io/">Verus Wiki</a> A wealth of How-to guides for Verus</li>
<li><a href="https://github.com/monkins1010/VerusPay">VerusPay</a> &amp; <a href="https://github.com/monkins1010/ChainTools">ChainTools</a> - Currently the most up to date software to use.</li>
</ul>
</li>
</ul>
<h2 id="getting-started">Getting Started</h2>
<h4 id="setting-up-your-wordpress-website">Setting up your WordPress Website</h4>
<ol>
<li>Goto <a href="https://cloud.digitalocean.com/">Digital Ocean</a> and setup an account, this <a href="https://m.do.co/c/cf6b23e11b50">Referal Link</a> will  get you $100 to spend over 60 days. After that the Plan we are loooking at is around $20 a month at time of writing June 19th 2020.</li>
<li>Create a Droplet (this is what Digital ocean call servers).</li>
</ol>
<p>Go to   <img src="https://github.com/monkins1010/Verusguideassets/raw/master/droplets.png" alt="Alt"> on the left hand panel in the Digital Ocean website.</p>
<p>At the top select<br>
<img src="https://github.com/monkins1010/Verusguideassets/raw/master/createdroplet.png" alt="Alt"></p>
<p>Then Pick</p>

