minecraft-sysvinit-script
=========================

Here is a script that you can copy to /etc/init.d/ to manage your Minecraft server.

I use it with Debian stable. YMMV with other distributions but I assume it'll work whereever sysvinit is used, or compatability provided.


INSTALLATION
------------

    # apt-get install tmux
    # cd /path/to/minecraft/server/
    # git clone https://github.com/Spidey01/minecraft-sysvinit-script.git
    # ln -s ./minecraft-sysvinit-script/minecraft /etc/init.d/minecraft
    # vi /etc/init.d/minecraft
    # update-rc.d minecraft defaults

You need to edit the scripts variables at the top. See below ;).


HELP
----

Call the script with long\_help as an argument. Or  use service. Here is the output as of commit 517c38393b321deeb0bceaff55db6039dd9cccdf:

    sudo service minecraft attach
        attach to server console.
      detach with control+b d
        see man tmux and Minecraft wiki for more info.

    sudo service minecraft backup
        backup the server.

    sudo service minecraft start
        start minecraft server.

    sudo service minecraft stop
        stop minecraft server.

    sudo service minecraft restart
        restart minecraft server.

    sudo service minecraft status
        check if running

    sudo service minecraft world {name of world to create or change to}
        change / create world.
        Default properties come from worlds/server.properties.defaults


    sudo service minecraft notify "message"
      Notify all players of message.

    sudo service minecraft update 1.7.4
      backup server and update to version 1.7.4.


CONFIGURATION
-------------

Edit the following variables in the script to configure it.


### SERVICE='minecraft'

Friendly name of the service. May be used in paths.


### USERNAME='minecraft'

The username that the server will run as.


### BACKUP\_ROOT="/usr/local/backups/Hosts/Centauri/srv/${SERVICE}/"

Where to store backups.


### MC\_ROOT='/srv/minecraft'

Path to Minecraft.


### MC\_JAR='minecraft\_server.jar'

Name of the JAR file to execute.


### MC\_SETTINGS="$MC\_ROOT/server.properties"


The properties file name to use. This will point to a link in $MC\_ROOT/worlds.


### JAVA\_FLAGS="-Xmx4G "


Command line flags to pass to the Java Runtime Environment.

-Xmx is the size of the initial memory pool. See `man java` and search for -Xmx.

### MC\_FLAGS='nogui'

Command line flags to pass to the Minecraft server. See the Minecraft wiki.


