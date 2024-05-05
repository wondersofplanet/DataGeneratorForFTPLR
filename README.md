Combined Log Generator
This Java program generates commands for creating log files and FTP log mover commands based on input files.

Input Files
inputServers.txt

This file contains a list of server names, with each server name listed on a separate line.

Example:

hostlist
server1.example.com
server2.example.com
server3.example.com



connection.txt
This file contains connection details for each server. Each line represents a connection with the format: connection_name,username,password,server.

Example:

userName,Password,ServerIPAddress,PortNo 
user1,password1,192.168.1.100,22
user2,password2,192.168.1.101,22


Output Files
createLogFilesCommands.txt for use in multissh program
This file contains commands for creating log files on each server. It includes commands to echo memory size and start vmstat.

Example:

server1.example.com echo Hello, the memory size of $(hostname -I) is $(awk '/MemTotal/ {print $2}' /proc/meminfo)
server1.example.com nohup vmstat 5 >> appname_log_May_05_server1.log &
server2.example.com echo Hello, the memory size of $(hostname -I) is $(awk '/MemTotal/ {print $2}' /proc/meminfo)
server2.example.com nohup vmstat 5 >> appname_log_May_05_server2.log &
server3.example.com echo Hello, the memory size of $(hostname -I) is $(awk '/MemTotal/ {print $2}' /proc/meminfo)
server3.example.com nohup vmstat 5 >> appname_log_May_05_server3.log &


forFTPLogMover.txt
This file contains FTP log mover commands for each server. It includes connection details and file paths.

Example:


server1.example.com,user1,password1,connection1,/home/batman/appname_log_May_05_server1.log,C:\abc
server2.example.com,user2,password2,connection2,/home/batman/appname_log_May_05_server2.log,C:\abc
