# Resolute-HackTHeBox-Write-Up

## Recon
### 1. Scanning with nmap.
### Script:
    ports=$(nmap -p- --min-rate=1000 -T4 10.10.10.169 | grep ^[0-9] | cut -d '/' -f 1 | tr '\n' ',' | sed s/, $//)
    nmap -sC -sV -p$ports 10.10.10.169
### Save our script as "start.sh" and run in terminal:
    sudo bash start.sh
### Waiting few minutes and looking on results:
    Starting Nmap 7.80 ( https://nmap.org ) at 2020-05-14 21:35 +07
    Nmap scan report for 10.10.10.169
    Host is up (0.15s latency).

    PORT      STATE  SERVICE      VERSION
    53/tcp    open   domain?
    88/tcp    open   kerberos-sec Microsoft Windows Kerberos (server time: 2020-05-14 14:45:57Z)
    135/tcp   open   msrpc        Microsoft Windows RPC
    139/tcp   open   netbios-ssn  Microsoft Windows netbios-ssn
    389/tcp   open   ldap         Microsoft Windows Active Directory LDAP (Domain: megabank.local)
    445/tcp   open   microsoft-ds Windows Server 2016 Standard 14393 microsoft-ds (workgroup: MEGABANK)
    464/tcp   open   kpasswd5?
    593/tcp   open   ncacn_http   Microsoft Windows RPC over HTTP 1.0
    636/tcp   open   tcpwrapped
    3268/tcp  open   ldap         Microsoft Windows Active Directory LDAP (Domain: megabank.local)
    3269/tcp  open   tcpwrapped
    5985/tcp  open   http         Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
        |_http-title: Not Found
    9389/tcp  open   mc-nmf       .NET Message Framing
    28531/tcp closed unknown
    47001/tcp open   http         Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
        |_http-server-header: Microsoft-HTTPAPI/2.0
            |_http-title: Not Found
    49664/tcp open   msrpc        Microsoft Windows RPC
    49665/tcp open   msrpc        Microsoft Windows RPC
    49666/tcp open   msrpc        Microsoft Windows RPC
    49667/tcp open   msrpc        Microsoft Windows RPC
    49671/tcp open   msrpc        Microsoft Windows RPC
    49676/tcp open   ncacn_http   Microsoft Windows RPC over HTTP 1.0
    49677/tcp open   msrpc        Microsoft Windows RPC
    49688/tcp open   msrpc        Microsoft Windows RPC
    49712/tcp open   msrpc        Microsoft Windows RPC
    53160/tcp open   unknown
    54651/tcp closed unknown
    Service Info: Host: RESOLUTE; OS: Windows; CPE: cpe:/o:microsoft:windows

    Host script results:
    |_clock-skew: mean: 2h30m39s, deviation: 4h02m30s, median: 10m38s
    | smb-os-discovery: 
    |   OS: Windows Server 2016 Standard 14393 (Windows Server 2016 Standard 6.3)
    |   Computer name: Resolute
    |   NetBIOS computer name: RESOLUTE\x00
    |   Domain name: megabank.local
    |   Forest name: megabank.local
    |   FQDN: Resolute.megabank.local
    |_  System time: 2020-05-14T07:46:49-07:00
    | smb-security-mode: 
    |   account_used: <blank>
    |   authentication_level: user  
    |   challenge_response: supported
    |_  message_signing: required
    | smb2-security-mode: 
    |   2.02: 
    |_    Message signing enabled and required
    | smb2-time: 
    |   date: 2020-05-14T14:46:48
    |_  start_date: 2020-05-14T13:24:52

### Nmap shows us, what 
