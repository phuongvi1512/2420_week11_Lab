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

[![Backup configuration file](/image/conf-file.png)]

Note:
> If you like to back up other directories, you can edit SOURCES variable in backup.conf

## Instruction

<ol>
    <li>To download files, use git clone command </li>
    <li>Create a directory named backup in /opt dir </li>
    <li>After downloading, move <strong>backup</strong> file to /opt/backup/ dir </li>
    <li>Move <strong>backup.conf</strong> file to /etc/systemd/ dir </li>
    <li>Move <strong>backup.timer and backup.service</strong> files to /etc/systemd/system/ dir </li>
    <li>To reload systemd files, run command sudo systemctl daemon-reload </li>
    <li>To start the service and timer files, run command
        <ul> 
            <li> sudo systemctl start backup.service </li> 
            <li>sudo systemctl start backup.timer </li>
        </ul>
    </li>
    <li>To check if service and timer files are properly set up, run command
        <ul>
            <li>systemctl status backup.service</li>
            <li>systemctl status backup.timer</li>
        </ul>
    </li>
</ol>

> The outcome should look like picture below
>
> ![backup.service status](/image/service-status.png)
> ![backup.timer status](/image/timer-status.png)

> Or you can run command systemctl list-timers to check if the timer file is run
>
> The outcome should have backup.timer file in the list
>
> ![timer list](/image/timer-units.png)

## Author
- Phuong Vi Dang A01292902
- Parnian Azarm A01245271
