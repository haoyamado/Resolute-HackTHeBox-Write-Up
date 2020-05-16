# Resolute-HackTHeBox-Write-Up

## Recon
### 1. Scanning with nmap.
### Script:
    ports=$(nmap -p- --min-rate=1000 -T4 10.10.10.169 | grep ^[0-9] | cut -d '/' -f 1 | tr '\n' ',' | sed s/, $//)
    nmap -sC -sV -p$ports 10.10.10.169
### Save our script as "start.sh" and run in terminal:
    sudo bash start.sh
### Waiting few minutes and looking on results:
    
