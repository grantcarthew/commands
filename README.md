# Command Cheat Sheet

## Linux

```shell
df -h  # Show free disk space
du -shc /var/*  # Show directory disk usage
du -h --max-depth=1 /var  # Show directory disk usage going one folder deep
du -h /var/ | sort -rh | head -5  # Show to five directory disk usage
resize2fs /dev/<device><partition> #[Linux] Resize the file system to an expanded partition
lsblk  # List block devices or disk devices and partitions

ssh-keygen -t ed25519 -C "<comment>"  # Generate a new SSH key pair
ssh-add  # Adds your SSH key to the SSH Agent (ssh-agent)

sed -i 's/old-text/new-text/g' input.txt  # Replace string in a text file globally case-sensitive
sed -i 's/old-text/new-text/gI' input.txt  # Replace string in a text file globally case-insensitive
sed -i 's/old-text/new-text/' input.txt  # Replace first instance of string in a text file
sed 's+http://+https://www.cyberciti.biz+g' input.txt  # Replace string in a text file globally case-sensitive different delimiter
sed -i -e '/FOO/s/love/sick/' input.txt  # Replace string in a text file once only if the line includes the word FOO

sudo apt update  # Downloads the latest package lists
sudo apt-get upgrade # Upgrade installed packages
sudo apt upgrade # Upgrade and install packages
sudo apt full-upgrade # Upgrades, installs, and removes packages

sudo dpkg -i $(curl -w "%{filename_effective}" -LO $(curl -s https://api.github.com/repos/bvaisvil/zenith/releases/latest | grep browser_download_url | cut -d '"' -f 4 | grep '64[.]deb$')) # Installs the latest package directly from a GitHub repo

sudo dhclient -r -v <interface name> && sudo rm /var/lib/dhcp/dhclient.* ; sudo dhclient -v <interface name>  # Release DHCP IP Address and renew
```

## SQL

```shell
sqlcmd -i <sql file> -U <user> -S <server address> -P <password> # Execute an SQL script
```

## Windows

```shell
wsl --list -v  # Show Windows Subsystem for Linux virtual machines
wsl --set-version <name> 2  # Set wsl distro to use WSLv2
```

## Container

```shell
docker exec -it <container name> /bin/sh  # Start a terminal into a running container (try /bin/bash)
docker exec -it <container name> <command>  # Execute a command in a running container
docker exec -it -e VAR=1 <container name> /bin/sh # Start a terminal with environment variables set
docker stats # Show running container statistics
docker logs <container id> # Display the standard out / error from within the container
docker logs <container id> -f # Follow the standard out / error

docker-compose up # Launch the services defined in the docker-compose.yml file
docker-compose up -d # Launch the services as a daemon
docker-compose ps # Show the running containers
docker-compose stop # Stop the services defined in the docker-compose.yml file
```

## VIM

```vim
:g/string/d " Deletes every line that contains <string>
```


