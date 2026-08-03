Linux commands Practice
-
File System command
--
1. **pwd** - Current working directory
2. **ls**  - list files
3. **ls -l**  - list files with details for ex permission 
4. **ls -a** - show hidden files
5. **mkdir** - make new directories
6. **rmdir**  - remove empty directory
7. **rm** - remove file
8. **rm -r** - remove directory recursively( all content in directory)
9. **cp <src> <dest>**- copy file
10. **cp -r <src> <Dest>** - copy directory recursively
11. **mv <src> <dest>** - move/rename file
12. **head** - show first 10 lines
      -> head file -n 2 -- show first 2 lines
14. **tail** - show last 10 lines
      -> tail file -n 2 - show last 2 lines


Networking troubleshooting
--
1. **ping <addr>** -  checking connectivity
2. **traceroute <addr?** - how packet travel from SRC to DEST (For ex. no. of station between src and dest)
3. **ip addr** - show my IP address
4. **ip route** - routing table
5. **ss -tuln** - currently which port listening
        -t -> TCP connection
         u -> UDP
         L -> listening port
         n -> IP address and port number
7. **netstat** - show open ports
8. **curl <url>** - get content from URL
9. **wget <url>** - download from URL
10. **ssh user@server-ip** -> to access instance
11. **dig** - DNS query (modern tool than nslookup)
12. **nslookup** - find mapping between DNS and ip address







