Most of the settings in bftpd are done by editing the file `/etc/bftpd.conf`. A default `/etc/xinetd.d/bftpd` configuration is provided as well.

`sudo pacman -S bftpd`


#### create ftp path:
`sudo mkdir /home/ftp`

#### create user ftper and verify it's home dir:
`sudo useradd -d /home/ftp ftper`
`sudo passwd ftper`

#### change owner of the dir:
`sudo chown ftper:ftper /home/ftp`

* * *
The bftpd.conf is a very explained file, all the variables are explained in detail, so it is easy to understand. If you want to know how my bftpd.conf is configured, take a look:

```js
  global {
    DENY_LOGIN="no"
    PORT="21"
    PASSIVE_PORTS="0"
    DATAPORT20="no"
    ADMIN_PASS="x"
    PATH_BFTPDUTMP="/var/run/bftpd/bftpdutmp"
    XFER_BUFSIZE="2048"
    CHANGE_BUFSIZE="no"
    XFER_DELAY="0"
    SHOW_HIDDEN_FILES="no"
    SHOW_NONREADABLE_FILES="no"
    ALLOW_FXP="no"
    CONTROL_TIMEOUT="300"
    DATA_TIMEOUT="30"
    RATIO="none"
    ROOTDIR="%h"   ## my dir = "/home/ftp"
    UMASK="022"
    LOGFILE="/var/log/bftpd.log"
    HELLO_STRING="ftp at %i ready."
    AUTO_CHDIR="/"
    AUTH="PASSWD"
    RESOLVE_CLIENT_IP="no"
    MOTD_GLOBAL="/etc/ftpmotd"
    MOTD_USER="/.ftpmotd"
    RESOLVE_UIDS="yes"
    DO_CHROOT="yes"
    LOG_WTMP="yes"
    BIND_TO_ADDR="any"
    PATH_FTPUSERS="/etc/ftpusers"
    AUTH_ETCSHELLS="no"
    ALLOWCOMMAND_DELE="no"
    ALLOWCOMMAND_STOR="yes"
    ALLOWCOMMAND_SITE="no"
    HIDE_GROUP=""
    QUIT_MSG="See you later..."
    USERLIMIT_GLOBAL="0"
    USERLIMIT_SINGLEUSER="0"
    USERLIMIT_HOST="0"
    GZ_UPLOAD="no"
    GZ_DOWNLOAD="no"
  }
  
  user ftp {
  #Any password fits.
   ANONYMOUS_USER="yes"
  }
  
  user anonymous {
  #If the client wants anonymous, ftp is taken instead.
   ALIAS="ftp"
  }
  
  user root {
   DENY_LOGIN="Root login not allowed."
  }
```

* * *

#### start bftpd service
`sudo systemctl start bftpd`

#### stop or restart bftpd service
`sudo systemctl stop/restart bftpd`

#### client login
enter  ftper/password to log in.




