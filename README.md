# phockup-docker-compose
A docker-compose .yml for ivandokov/phockup.

Documentation for Phockup can be found at https://github.com/ivandokov/phockup. 

``` version: "2.2"
services:
  phockup:
    image: ivandokov/phockup:latest
    container_name: phockup
    command: /mnt/unsorted-imports /mnt/sorted-imports --move --date YYYY/YYYY-MM # you can edit the folder names.
    volumes:
      - ~/Pictures:/mnt # edit this line for your system
    restart: unless-stopped
```
### Usage

Copy the block of text above by clicking the "copy" button in the top right corner. 

This can be used with normal docker-compose, or you can create a [stack](https://www.portainer.io/blog/stacks-docker-compose-the-portainer-way) in [Portainer](https://www.portainer.io/) with it. 

The arguments I put in will move the items from the unsorted folder to the sorted folder (--move), and the ```--date YYYY/YYYY-MM``` will make a folder with the year, and then other folders inside it, named year-month. (e.g., ```2022/2022-07```. You can edit the ```command``` line in the .yml to use whatever other phockup arguments you like. 

### Notes:

Every time the container is restarted, The actions specified in the line called ```command:``` will be run. If you leave the ```restart: unless-stopped``` at the end, this container will ceaselessly run and restart. If you don't need it constantly running, comment out the last line with a ```#```, and make a cron job to restart the container as often as you would like the import folder to be checked for more items. 

### Credits:

Thanks to @km0201#8526 on discord for initially converting the docker-run to docker-compose. 

OpenMediaVault Discord server: https://discord.gg/qcGj2upevS
