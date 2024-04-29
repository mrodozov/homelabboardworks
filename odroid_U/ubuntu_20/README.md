## homelabboardworks
Settings and howtos/whattos for my single board computers

## Odroid-U - Ubuntu 20 server

* **Donwloaded**: Get the image from here:
https://github.com/RKaczmarek/imagebuilder/releases/download/0.0.1/odroid_u3-armv7l-ubuntu20.04minimal-1601403301.zip

## Install
unzip -e odroid_u3-armv7l-ubuntu20.04minimal-1601403301.zip


## Post install:
sudo apt-get install curl wget
# install docker
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

## Post-install on SSD drive:

#Image location on local drive: 960 GB drive
odroid_images/odroid_u/odroid_u3-armv7l-ubuntu20.04minimal-1601403301.zip


