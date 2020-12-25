## **PORT KILLING**

#### sudo kill

####  `sudo lsof -t -i:port`

#### sudo kill

####  `sudo lsof -t -i:3000`

#### KILL ALL THE NODE PORTS

`killall -9 node`

#### CHMOD

* If you are going for a console command it would be:

​          `chmod -R 777 /www/store`. The -R (or --recursive) options make it recursive.

* Or if you want to make all the files in the current directory have all permissions type:

​         `chmod -R 777 ./`

#### TO INSTALL AND UPDATE THE POSTMAN

`sudo snap install postman`

`sudo snap switch --channel=candidate postman`

`sudo snap refresh postman`

#### INSTALL JAVA IN UBUNTU

[Download](https://linuxize.com/post/install-java-on-ubuntu-18-04/)

#### REMOVE ALL NODE MODULES GLOBALLY

`npm ls -gp --depth=0 | awk -F/ '/node_modules/ && !/\/npm$/ {print $NF}' | xargs npm -g rm`

#### ADDING ALIAS IN UBUNTU

`alias our_command='actual command'`

 

## **GIT Commands**

#### Knowing the logged user

`git config user.email`

`git config --list `



#### SETTING GIT CONFIG

`git config --global user.email [your email address here]`

`git config --global user.name [name here]`

 

#### GIT PULL

`git pull origin [branch name]`