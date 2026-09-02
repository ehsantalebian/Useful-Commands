# General Commands

Here are some sets of General commands that can assist you in your day-to-day activities.

- Find Active Services
```bash
netstat -lntup OR ps -aux
```

- Find a File
```bash
find . -iname [File Name]*
```

- List of Active Services
```bash
ps -aux | grep -i [uwsgi or runserver or puma] | awk '{print $2}' | xargs pwdx
```

- See Directories Size
```bash
du -hsx $PWD/* | sort -rh | head -n 40
```

- Show Logs of a Specific Word and File
```bash
LC_ALL=C fgrep -C 15 '[Words to Search]' [Log File Path]
```

- List Deleted but Running Files
```bash
lsof +aL1 /data
```

- TCP Dump Command
```bash
tcpdump -i [Network Interface] dst [Destination IP] -v -t -X
```

- Add Date to DB Backup File Name
```bash
-$(date +"%b-%d-%Y-%H-%M").sql
```

- Add Date to File Name
```bash
-$(date +"%Y-%b-%d")
```

- OVF Export
Sample
```bash
ovftool.exe vi://[IP]/[Machine Name] [Extraction Path]
```
Example
```bash
ovftool.exe vi://172.16.1.64/BigBlueButton C:\OVFs
```

- Check Security
```bash
nmap --script +ssl-enum-ciphers -p 443 [URL] | egrep "SSLv|TLSv"
```

```bash
openssl s_client -connect [URL]:443 -tls[TLS Version]
```
