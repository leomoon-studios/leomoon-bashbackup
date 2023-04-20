## Introduction
BashBackup is a reliable backup system for Linux. With BashBackup you can automate database and folder backups and upload them to another FTP or Dropbox. By combining BashBackup with Linux Cron, you can setup backup schedules and fully automate this process.

## Features
- Automatic backup of mySQL database(s)
- Automatic backup of folder(s) with exclusions
- Automatic upload of all backups to another FTP
- Automatic upload of all backups to Dropbox using Dropbox access token
- Password protected zip (optional)
- Keeping last x number of backups
- Custom compression ratio

## Authors
- Amin Babaeipanah

## Changelog
- 3.0.0 2023-04-15: Rewrite of bashbackup.

## Arguments
```
-n|--name           File name of the zipped backup.
                    Timestamp will be appended to the name.
-b|--backup         Path to backup.
--database-type     Define database type to backup. Default = mysql
--database-host     Define database host to backup. Default = localhost
--database-name     Define database name to backup.
--database-user     Define database user to backup.
--database-pass     Define database password to backup.
-e|--exclude        Backup exclude. Supports wildcards.
-t|--to-path        Backup destination path. Default = /var/backup
-k|--to-keep        Number of backups to keep. Default = 7
-d|--dropbox-key    Dropbox access token.
--ftp-host          FTP IP/URL.
--ftp-user          FTP user.
--ftp-pass          FTP password.
-p|--zip-password   Password to encrypt backup archive.
-c|--compression    Compression level 0-9. Default is 5.
-q|--quiet          Quiet operation.
```

## Script Setup
- Download the script to your desired location.
- Make a [Dropbox app](https://www.dropbox.com/developers/apps) and get a Dropbox access token if you also want to upload backups to Dropbox.
- Create `.env` file where bashbackup is saved to store zip password, dropbox key, database password, etc.

  Email alerts on failed backups is also supported but postfix must be configured on the server. Remove `bb_email_alert_from` and `bb_email_alert_to` if you don't want email alerts.

  ```text
  bb_email_alert_from='from@domain.com'
  bb_email_alert_to='to@domain.com'
  bb_dropbox_key='<dropbox_key>'
  bb_zip_password='<zip_password>'
  bb_db_wordpress='<wordpress_db_password>'
  ```

## Cron Examples
In these examples, bashbackup is stored at `/bashbackup/bb` and the env file is stored at `/bashbackup/.env`.

Backup `"$HOME/folder"`, exluding `zip` files and `bin` folder to Dropbox with zip password (don't miss the dot in the beginning):
```
. /bashbackup/.env && /bashbackup/bb -n "backup-name" -b "$HOME/folder" -e "*.zip" -e "*/bin/* -d $bb_dropbox_key -p $bb_zip_password
```

Backup mysql database to Dropbox with zip password (don't miss the dot in the beginning):
```
. /bashbackup/.env && /bashbackup/bb -n "backup-name" --database-name "wordpress" --database-user "user" --database-pass $bb_db_wordpress -d $bb_dropbox_key -p $bb_zip_password
```

## Compatibility
Tested on cPanel 66.0.24, Ubuntu 22.04
