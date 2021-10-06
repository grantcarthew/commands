# Command Cheat Sheet

This page is my long term memory of command line tools.

Another great resource is [tldr pages](https://tldr.sh/).

## Linux

```shell
df -h  # Show free disk space
du -shc /var/*  # Show directory disk usage
du -h --max-depth=1 /var  # Show directory disk usage going one folder deep
du -h /var/ | sort -rh | head -5  # Show to five directory disk usage
resize2fs /dev/<device><partition> #[Linux] Resize the file system to an expanded partition
lsblk  # List block devices or disk devices and partitions

find -name "<search string>*" -exec mv -t ./<target dir>/ {} + # Move all the found files to the target dir

watch <command> # Runs the command at a 2 second interval displaying result

ssh-keygen -t ed25519 -C "<comment>"  # Generate a new SSH key pair
ssh-add  # Adds your SSH key to the SSH Agent (ssh-agent)

sed -i 's/old-text/new-text/g' input.txt  # Replace string in a text file globally case-sensitive
sed -i 's/old-text/new-text/gI' input.txt  # Replace string in a text file globally case-insensitive
sed -i 's/old-text/new-text/' input.txt  # Replace first instance of string in a text file
sed 's+http://+https://www.example.com+g' input.txt  # Replace string in a text file globally case-sensitive different delimiter
sed -i -e '/FOO/s/love/sick/' input.txt  # Replace string in a text file once only if the line includes the word FOO
sed -i 's/\r$//g' input.txt # Replaces CR leaving just the LF at the end of the lines

sudo apt update  # Downloads the latest package lists
sudo apt-get upgrade # Upgrade installed packages
sudo apt upgrade # Upgrade and install packages
sudo apt full-upgrade # Upgrades, installs, and removes packages

sudo dpkg -i $(curl -w "%{filename_effective}" -LO $(curl -s https://api.github.com/repos/bvaisvil/zenith/releases/latest | grep browser_download_url | cut -d '"' -f 4 | grep '64[.]deb$')) # Installs the latest package directly from a GitHub repo

sudo dhclient -r -v <interface name> && sudo rm /var/lib/dhcp/dhclient.* ; sudo dhclient -v <interface name>  # Release DHCP IP Address and renew
```

## Git

```shell
git status # Show the repository status
git diff # Show the file differences in the working tree
git diff --staged # Show the file differences in staged files
git checkout -b <name> # Create a new branch and switch to it
git add . # Stage all changed files for commiting
git add <file path> # Stage the file for commiting
git add <file path>\* # Stage all the files in the directory for commiting
git merge <branch> # Merges the changes in <branch> into the current branch
git commit -m "<messabe" # Commit the staged files into the local repository
git push origin <branch> # Push the local repository changes up to the origin
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

## Cloud

```shell
terraform force-unlock -force <lock id> # Removes a lock from the state
```

## Container

```shell
docker login # Login to the public Docker container registry
docker login <repository address> # Login to a container registry
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

kubectl logs <pod name> # Display the logs from a pod
kubectl logs <pod name> -f # Follow the logs from a K8s pod
kubectl logs --previous <pod name> <container name> # Display the logs from the previous running container
kubectl delete pod <pod name> # Restart a pod if deployment unchanged
kubectl exec -it <pod name> -- sh # Start an interactive shell into a running single container pod
kubectl exec <pod name> -- sh -c 'echo $<env variable name>' # Display a pod environment variable
kubectl get deployment --output yaml # Print the current deployment to the terminal

helm install <release name> <chart name> # Installs a new package into the K8s cluster
helm install <release name> <chart directory> # Installs a new package from an unpacked chart
helm install <chart name> --generate-name # Installs a new package generating a release name
helm install -f <values yml> <release name> <chart name> # Installs a new package with custom configuration
helm install --set key=value,key2=value2,outer.inner=value,list={a,b,c},list[0].key=value <release name> <chart name> # Installs a new package with custom configuration
helm status <release name> # Display a deployed charts information
helm show values <chart name> # Displays configurable options
helm get values <chart name> # Displays the user supplied values
helm upgrade -f <values yml> <release name> <chart name> # Upgrade the chart or configuration
```

## VIM

```vim
h " Move cursor left
j " Move cursor down
k " Move cursor up
l " Move cursor right
gg " Go to the top
G " Go to the bottom
w " Move forward a word
b " Move back a word
% " Move between brackets

v " Select
V " Select line
y " Copy selected
p " paste selected

q<letter> " Starts recording a macro
q " Finishes recording a macro
@<letter> " Executes a macro

x " Delete a character
dd " Delete line
:g/string/d " Delete all lines that contain string

o " New line below
O " New line above

:g/string/d " Deletes every line that contains <string>
```


