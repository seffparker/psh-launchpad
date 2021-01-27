# psh-launchpad
An interactive BASH script to search/select servers to SSH into.

```
     +----------------+       +----------------+       +----------------+
     |                |       |                |       |                |
     |   PSH Client   | ----> |   PSH Server   | ----> |   SSH Server   |
     |                |       |                |       |                |
     +----------------+       +----------------+       +----------------+
```

# PSH Menu Preview
![PSH Menu Preview](https://raw.githubusercontent.com/seffparker/psh-launchpad/master/psh-menu-screen-1.png "PSH Menu Preview")

# Features
- Compatible with all exising SSH login menthods like password, publickey, or 2FA.
- Pass the argument right from the SSH client machine.
- Logs all logins, logout, and SSH session logs
- History with custom record count

# Usage
```
psh-client [argument]
```
The argument can be any of the following:
 - FQDN
 - IP address
 - A hosted domain (the rDNS of Domain's A record should be an FQDN)
 - The filename of the stored SSH command
 - Partial match in the stored SSH command (SSH username, port, IP, or hostname)

# Usage Examples:
```
psh-client # show the top menu
psh-client 123.22.33.44
psh-client hostname.tld
psh-client hosted-domain.com
psh-client my-dev-server # filename
psh-client dev # partial text match
```
If multiple macthes are found, a menu will be generated with matched records.

# Logs
/var/log/psh/login.log:
```
[2021-01-27 10:17:25 UTC] - ssh_user 123.22.33.44: Logging into server-group/hostname (Session ID: 1000-6229-11280
[2021-01-27 10:19:24 UTC] - ssh_user 123.22.33.44: Logout from server-group/hostname (Exit code: 0, Duration: 00h:01m:59s, Session ID: 1000-6229-11280)
```
/var/log/psh/session/server-group/hostname/hostname-ssh_user-1000-6229-11280-20210127_1017.log:
```
..
(logs all SSH session logs in real-time)
..
```
