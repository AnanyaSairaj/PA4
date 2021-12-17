# ASSIGNMENT 4: DISTRIBUTED FILE SYSTEMS
## Objective : To create a file system for reliable and secure file storage.
The program handles multiple requests form the clients concurrently using fork().
The requests handled are GET ,PUT and LIST.

Client and server have unique configuration files which are parsed and then authenticated. This authentication is supposed to be done before every function call.

## Requests Handled
GET: From the client side we send a request to the server with the name of the file to be fetched. If the file is not present, the server sends back an error. If the file is present it checks for the authentication and if the authentication is successfull ,it sends the file part requested. Since the file is broken into to 4 parts and they are uploaded in the 4 distributed servers each part has to be requested from the particular server.


PUT: From the client side we send the file to be uploaded into the four different servers. The file is broken into 4 almost equal parts and uploaded into the distributed servers .The authentication is also done so as to provide security and redundancy.


LIST: This request is sent from the client side and the server responds by listing all the files present in it's directories.

mkdir: Creates subdirectory in the dfs directories.

Encrytion: Basic XOR encryption was done before sending the file and also done in the server side also before sending it.
## Instructions 

First run make seperately on both client and server
Once the compilation is done ,the server and client executables can be run in the following manner.

### Server
```
cd [SERVER]
make
./server [local-conf-folder] [PORT NUMBER][local directory]
example: ./server dfs.conf 10001 dfs1
./server dfs.conf 10002 dfs2
./server dfs.conf 10003 dfs3
./server dfs.conf 10004 dfs4
```
First open all 4 servers and then the client
### Client
```
cd [CLIENT]
make
./client [local-conf-folder]
example: ./client dfc.conf

example of request:
First execute put,then get.
put foo1.txt
get foo1.txt
list
mkdir TEST
put foo1.txt TEST/
get foo1.txt TEST/
exit.
```
