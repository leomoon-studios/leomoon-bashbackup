## Introduction

Bash2Cloud is our in-house script to automate file and database backups on our Linux servers.

Zip file includes two files:

*   sql2cloud is used to automate database backup
*   dir2cloud is used to automate files and folders backup

## Features

*   Automatic backup of database(s)
*   Automatic backup of file(s) and folder(s) with exclusions
*   Automatic upload of all backups to another FTP
*   Automatic upload of all backups to Dropbox using Dropbox access token
*   Custom compression ratio

## Donations

Future development of this project depends on community donations. All proceeds will go towards the development. You can donate using [[THIS LINK]](https://www.paypal.me/aminpersia) and make sure to include which project you want to support.

## Donors

*   NA

## Programmers

*   Amin Babaeipanah

## Changelog

*   sql2cloud 0.30:
    *   Added error check
*   sql2cloud 0.29:
    *   Initial release
*   dir2cloud 0.18:
    *   Added error check
*   dir2cloud 0.17:
    *   Initial release

## How to install

1.  Make a [Dropbox app](https://www.dropbox.com/developers/apps) and get a Dropbox access token if you also want to upload backups to Dropbox
2.  Read the INFO section of each script

## Future ideas

*   NA

## Compatibility

Tested on cPanel 66.0.24, Ubuntu 14.04, 16.04
