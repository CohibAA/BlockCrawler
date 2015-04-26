This is a fork of CallMeJake's BlockCrawler
https://github.com/CallMeJake/BlockCrawler

The API support is NOT included in this fork.

Some of the changes implemented in this fork are in production on
https://bitcoin-p2pool.com/bitcoin_block_explorer/

Block Crawler Install Instructions

Get all of the following files and place them in your public html folder for the block crawler:

	block_crawler.php - The home page for the script.
	block_crawler.css - The CSS Style Sheet for the script.
	bc_layout.php - This file contains most of the php.html used to render the site.
	bc_daemon.php - This file contains fucntions for interacting with the daemon.

Debian Ubuntu 14.04 Example:

	cd /var/www/example.com/public_html
	git clone https://github.com/CohibAA/BlockCrawler.git
	cd BlockCrawler
	nano bc_daemon.php

Find the bc_daemon.php and open it in your text editor or PHP IDE.  At the
top you will find the following code:

/******************************************************************************
	Wallet Configuration
******************************************************************************/
	$GLOBALS["wallet_ip"] = "127.0.0.1";
	$GLOBALS["wallet_port"] = "8332";
	$GLOBALS["wallet_user"] = "rpcusername-from-bitcoin-conf";
	$GLOBALS["wallet_pass"] = "rpcpassword-from-bitcoin-conf";
	
It is important to replace these values with the correct information for your wallet daemon.

The daemon will work with RPCSSL configured if your version of cURL supports it.

You may need to install and enable php and php-curl if using Apache2 to host the crawler.

	sudo apt-get install libapache2-mod-php5
	sudo apt-get install php5-curl

Here are some sample entries for the value $GLOBALS["wallet_ip"]:

	"127.0.0.1" - This will communitcate with the daemon in clear text
	"http://127.0.0.1" - This is also an unencrypted connection
	"https://127.0.0.1" - This will connect to the wallet using SSL encryption.

Once you have made these changes upload the files to your server. You should be ready to go.
