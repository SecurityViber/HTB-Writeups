# Box: Knife

## Reconnaissance

### Information Disclosure

Using Wappalyzer on the web app revealed:
- Apache HTTP Server 2.4.41
- PHP 8.1.0-dev
- OS: Ubuntu

### Nmap

```
sudo nmap -T4 -p- -A 10.10.10.242
```

```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-11-26 10:44 CET
Nmap scan report for 10.10.10.242
Host is up (0.030s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   3072 be:54:9c:a3:67:c3:15:c3:64:71:7f:6a:53:4a:4c:21 (RSA)
|   256 bf:8a:3f:d4:06:e9:2e:87:4e:c9:7e:ab:22:0e:c0:ee (ECDSA)
|_  256 1a:de:a1:cc:37:ce:53:bb:1b:fb:2b:0b:ad:b3:f6:84 (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title:  Emergent Medical Idea
Device type: general purpose
Running: Linux 5.X
OS CPE: cpe:/o:linux:linux_kernel:5.0
OS details: Linux 5.0
Network Distance: 2 hops
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 1025/tcp)
HOP RTT      ADDRESS
1   29.21 ms 10.10.14.1
2   29.56 ms 10.10.10.242

Nmap done: 1 IP address (1 host up) scanned in 23.64 seconds
```

## Enumeration

### Port 80 — HTTP

#### Dirsearch

```
dirsearch -u http://10.10.10.242
```

```
Extensions: php, aspx, jsp, html, js | HTTP method: GET | Threads: 25 | Wordlist size: 11460

Target: http://10.10.10.242/

[10:49:25] Starting:
[10:49:27] 403 -  277B  - /.ht_wsr.txt
[10:49:27] 403 -  277B  - /.htaccess.bak1
[10:49:27] 403 -  277B  - /.htaccess.orig
[10:49:27] 403 -  277B  - /.htaccess.sample
[10:49:27] 403 -  277B  - /.htaccess.save
[10:49:27] 403 -  277B  - /.htaccess_extra
[10:49:27] 403 -  277B  - /.htaccess_orig
[10:49:27] 403 -  277B  - /.htaccessBAK
[10:49:27] 403 -  277B  - /.htaccess_sc
[10:49:27] 403 -  277B  - /.htaccessOLD
[10:49:27] 403 -  277B  - /.htaccessOLD2
[10:49:27] 403 -  277B  - /.html
[10:49:27] 403 -  277B  - /.htm
[10:49:27] 403 -  277B  - /.httr-oauth
[10:49:27] 403 -  277B  - /.htpasswds
[10:49:27] 403 -  277B  - /.htpasswd_test
[10:49:45] 403 -  277B  - /server-status/
[10:49:45] 403 -  277B  - /server-status

Task Completed
```

## Exploitation

PHP 8.1.0-dev ships with a backdoor in the `User-Agentt` header that allows unauthenticated RCE.

References:
- [PHP 8.1.0-dev — 'User-Agentt' RCE (ExploitDB 49933)](https://www.exploit-db.com/exploits/49933)
- [Medium write-up](https://amsghimire.medium.com/php-8-1-0-dev-backdoor-cb224e7f5914)

## Privilege Escalation

Run `sudo -l` to list sudoable binaries. `knife` will be listed. Look it up on [GTFOBins](https://gtfobins.github.io/) to get a root shell.
