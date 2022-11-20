# Readme file for how to use backup

## Usage

Using timer and service file to automatically back up user home directory, user /etc/ dir and /opt dir into a remote server

## Files included

- **backup**: script used to backup
- **backup.conf**: configuration file to store variables in backup
- **backup.service**: service unit file used to trigger backup script 
- **backup.timer**: timer unit file to trigger backup.service file at Friday, 1 am

## Prerequisites

- IP address of the remote server
- the key of the server must be in authorized_keys in remote server /.ssh dir
- vim or nano text editor to edit files
- ssh to connect to remote server
- username of remote server and the host must be the same
- Both servers must have rsync utility

## Variables

Before starting, in backup.conf, please change
- USER variable to server username
- IPADDRESS to remote server's IP address

Note:
> If you like to back up other directories, you can edit SOURCES variable in backup.conf

## Instruction

<ol>
    <li>To download files, use git clone command </li>
    <li>Create a directory named backup in /opt dir </li>
    <li>After downloading, move **backup** file to /opt/backup/ dir </li>
    <li>move **backup.conf** file to /etc/systemd/ dir </li>
    <li>move **backup.timer** and **backup.service** files to /etc/systemd/system/ dir </li>
    <li>To reload systemd files, run command ==sudo systemctl daemon-reload== </li>
    <li>To start the service and timer files, run command ==sudo systemctl start backup.service== ==sudo systemctl start backup.timer== </li>
    
</ol>