.. _setup-production-nginx:

Deploy OpenERP on NGINX 
=======================
.. note::
	Part of this page is taken from http://www.schenkels.nl
	
As we advice that for production setup Linux is the preferred Operating System, It is an essential to configure OpenERP as an linux server after the installation. 

OpenERP can be install on any linux system based on ``.deb`` or ``.rpm``, please go through below installation steps for Linux and Mac.

* :ref:`Install OpenERP on Ubuntu Desktop or Server <install-ubuntu>`
* :ref:`Install OpenERP on Fedora, CentOS <install-fedora>`
* :ref:`Install OpenERP on Mac OSX 10.X.X <install-macosx>`

After successfully installation, you can configure the server to be started automatically at boot time, so :ref:`install it as a service <setup-production-openerp-service>`.

Start with the installation of NGINX, Create your cert and key First create a temporary directory and move the files to their final resting

Installation of NGINX
---------------------

.. code-block:: bash

	$ sudo apt-get install nginx
	
Create your cert and key
------------------------
First create a temporary directory and move the files to their final resting place once they have been built (the first cd is just to make sure we are in our home directory to start with):

.. code-block:: bash
	
	cd
	mkdir temp
	cd temp

Generate a new key, you will be asked to enter a passphrase and confirm:

.. code-block:: bash
	
	openssl genrsa -des3 -out server.pkey 1024

Remove the passphrase by doing this, we do this because we don't won't to have to type this passphrase after every restart.

.. code-block:: bash
	
	openssl rsa -in server.pkey -out server.key

Next we need to create a signing request which will hold the data that will be visible in your final certificate:

.. code-block:: bash
	
	openssl req -new -key server.key -out server.csr

This will generate a series of prompts like this: Enter the information as requested. And finally we self-sign our certificate.

.. code-block:: bash
	
	openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt

We only need two of the files in the working directory, the key and the certificate. But before we can use them they need to have their ownership and access rights altered:

.. code-block:: bash
	
	sudo chown root:www-data server.crt server.key
	sudo chmod 640 server.crt server.key

And then we put them in a sensible place:

.. code-block:: bash
	
	sudo mkdir /etc/ssl/nginx
	sudo chown www-data:root /etc/ssl/nginx
	sudo chmod 710 /etc/ssl/nginx
	sudo mv server.crt server.key /etc/ssl/nginx/

We now have the key and certificate on the final location. We can now tell nginx where the files are and how they will behave.

Create the nginx site
---------------------
We create a new configuration file
sudo nano /etc/nginx/sites-available/openerp

with the following content:

.. warning::

	You will need to change all references to openerpserver.example.com in the following file to either the domain name or static IP address of your server.

.. code-block:: bash
	
	upstream webserver {
	    server 127.0.0.1:8069 weight=1 fail_timeout=300s;
	}
	
	server {
	    listen 80;
	    server_name    _;
	
	    # Strict Transport Security
	    add_header Strict-Transport-Security max-age=2592000;
	
	    rewrite ^/.*$ https://$host$request_uri? permanent;
	}
	
	server {
	    # server port and name
	    listen        443 default;
	    server_name   openerpserver.example.com;
	
	    # Specifies the maximum accepted body size of a client request,
	    # as indicated by the request header Content-Length.
	    client_max_body_size 200m;
	
	    # ssl log files
	    access_log    /var/log/nginx/openerp-access.log;
	    error_log    /var/log/nginx/openerp-error.log;
	
	    # ssl certificate files
	    ssl on;
	    ssl_certificate        /etc/ssl/nginx/server.crt;
	    ssl_certificate_key    /etc/ssl/nginx/server.key;
	
	    # add ssl specific settings
	    keepalive_timeout    60;
	
	    # limit ciphers
	    ssl_ciphers            HIGH:!ADH:!MD5;
	    ssl_protocols            SSLv3 TLSv1;
	    ssl_prefer_server_ciphers    on;
	
	    # increase proxy buffer to handle some OpenERP web requests
	    proxy_buffers 16 64k;
	    proxy_buffer_size 128k;
	
	    location / {
	        proxy_pass    http://webserver;
	        # force timeouts if the backend dies
	        proxy_next_upstream error timeout invalid_header http_500 http_502 http_503;
	
	        # set headers
	        proxy_set_header Host $host;
	        proxy_set_header X-Real-IP $remote_addr;
	        proxy_set_header X-Forward-For $proxy_add_x_forwarded_for;
	
	        # Let the OpenERP web service know that we're using HTTPS, otherwise
	        # it will generate URL using http:// and not https://
	        proxy_set_header X-Forwarded-Proto https;
	
	        # by default, do not forward anything
	        proxy_redirect off;
	    }
	
	    # cache some static data in memory for 60mins.
	    # under heavy load this should relieve stress on the OpenERP web interface a bit.
	    location ~* /web/static/ {
	        proxy_cache_valid 200 60m;
	        proxy_buffering    on;
	        expires 864000;
	        proxy_pass http://webserver;
	    }
	
	}
	
We then will enable the new site configuration by creating a symbolic link in the /etc/nginx/sites-enabled directory.

.. code-block:: bash
	
	sudo ln -s /etc/nginx/sites-available/openerp /etc/nginx/sites-enabled/openerp

Change the OpenERP server configuration file

We now need to re-configure the openerp server in a way that non-encrypted services are not accessible from the outside world.

We will change the /etc/openerp-server.conf so that it will only except requests from nginx.

Just open then file and add 127.0.0.1 to the xmlrpc and netrpc interface lines as shown below.

.. code-block:: bash
	
	sudo vi /etc/openerp-server.conf
	
	xmlrpc_interface = 127.0.0.1
	netrpc_interface = 127.0.0.1
	
Try the new configuration
-------------------------
Restart the services to load the new configurations

.. code-block:: bash
	
	sudo service openerp-server restart
	sudo service nginx restart

You should not be able to connect to the web client on port 8069. For web access you just need to visit https://openerpserver.example.com