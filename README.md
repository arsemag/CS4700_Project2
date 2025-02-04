Code Organization:
main: 
This is the entry point of the program, where the argparse library is used to handle command-line arguments. Based on the operation and URL provided, it will establish a connection to the FTP server and execute the corresponding FTP command.

send_command(sock, command): 
This function is responsible for sending commands to the FTP server and receiving the response.
It encodes the command, sends it to the server, and decodes the response.

connect_to_ftp(user, pwd, port=21): 
This function establishes a connection to the FTP server using the provided username, password, and port. 
It handles the authentication process and returns the connected socket.

pasv_command(socks): 
This function sends the PASV command to the 
server to initiate passive mode and receive a new data connection. It returns a new data socket for file transfers.

list_command(socks): 
This function lists the contents of a directory on the FTP server by sending the LIST command.
It receives the data through the passive connection and prints the directory contents.

dele_command(socks, filename): 
This function sends the DELE command to remove a file from the server.

mkd_command(socks, dir_name): 
This function sends the MKD command to create a new directory on the server.

rmd_command(socks, dir_name): 
This function sends the RMD command to remove a directory from the server.

stor_command(socks, file_sor, file_dest): 
This function uploads a file to the FTP server by sending the STOR command.
It uses the data channel to transfer the file in chunks. This is when we get a 
file from our local machine and store it onto the server

retr_command(socks, file_source, file_dest): This function downloads a file from the FTP server 
using the RETR command. It receives the file data through the data channel and saves it locally.

quit_command(socks): This function sends the QUIT command to the server to gracefully close the connection.


Testing: 
I uploaded files and created directories on the server to ensure proper storing and retrieving files. 
Personally the difficulties I encountered were the STOR and RETR commands because my inputs were to poorly labeled so 
there were times when I was not storing properly therefore, the RETR command would not work. Also for testing I add 
some print statements to ensure that the outputs and inputs were what I was expecting. 