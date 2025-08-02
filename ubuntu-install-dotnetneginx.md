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
