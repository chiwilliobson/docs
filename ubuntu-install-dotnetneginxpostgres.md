# Postgres
### Install postgres in ubuntu
... use copilot

### Coonfigure postgres SSL
sudo find /etc/postgresql -name "postgresql.conf"
/etc/postgresql/16/main/postgresql.conf

### Generate a private key
sudo openssl genrsa -des3 -out server.key 2048

### Generate a Certificate Signing Request (CSR)
sudo openssl req -new -key server.key -out server.csr

### Generate the self-signed certificate
openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt

### You'll need to remove the passphrase from the private key if you don't want to enter it every time the PostgreSQL server starts.
openssl rsa -in server.key -out server.key.unencrypted
mv server.key.unencrypted server.key


### Configure Postgres

----------------
sudo nano /etc/postgresql/16/main/postgresql.conf

ssl = on

ssl_cert_file = '/etc/postgresql/16/main/server.crt'

ssl_key_file = '/etc/postgresql/16/main/server.key'

listen_addresses = '*'		# what IP address(es) to listen on;

---------------
sudo nano /etc/postgresql/16/main/pg_hba.conf

$# TYPE DATABASE  USER      ADDRESS      METHOD  OPTIONS

hostssl all      all       0.0.0.0/0    scram-sha-256


## Dotnet and Nginx

# Update the package list to ensure you have the latest information
sudo apt-get update && sudo apt-get install -y software-properties-common

# Add the .NET backports repository for access to newer .NET versions
sudo add-apt-repository ppa:dotnet/backports

# Update the package list again to include the new repository
sudo apt-get update

# Install the .NET SDK (Software Development Kit). Replace '9.0' with the specific version you need.
# The SDK includes the runtime, so you don't typically need to install the runtime separately.
sudo apt-get install -y dotnet-sdk-9.0

# Install NGINX web server
sudo apt install nginx

# Start the NGINX service immediately
sudo systemctl start nginx

# Enable NGINX to start automatically on system boot
sudo systemctl enable nginx




