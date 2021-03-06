# TCPIPUsingSSLSocket

This project contains two files - TLSServerTestDrive.java and EchoClient.java. TLSServerTestDrive.java is to be run on server, while EchoClient.java runs on client.

1. Generate keys in both server and client as follows. The working directories are /opt/sslsocket for the server, and project's root directory for the client respectively.
- Server: keytool -genkey -v -keystore server.jks -alias server_private -keyalg RSA -keysize 1024 -validity 365
- Client: keytool -genkey -v -keystore client.jks -alias client_private -keyalg RSA -keysize 1024 -validity 365 

2. Export certificates
- Server: keytool -export -alias server_private -keystore server.jks -rfc -file trustServer.cer
- Client: keytool -export -alias client_private -keystore client.jks -rfc -file trustClient.cer

3. Copy the .cer files from step 2 above to each other (copy trustServer.cer to the client and trustClient.cer to the server).

4. Import keystore
- Server: keytool -import -alias trustClient -file trustClient.cer -keystore server.jks
- Client: keytool -import -alias trustServer -file trustServer.cer -keystore client.jks

5. Compile and run the server-side programme first (TLSServerTestDrive.java) and then do the same with the client-side programme (EchoClient.java).

## Screenshots
If you have a look at each screenshot below, you can find the client sending 'hello' to the server and the server is receiving that message.

(1) Client-side
![screenshot from 2018-04-04 17-04-43](https://user-images.githubusercontent.com/35015246/43180278-1f30ab1e-9012-11e8-9fb8-88a05e3e0904.png)

(2) Server-side
![screenshot from 2018-04-04 17-07-46](https://user-images.githubusercontent.com/35015246/43180289-2cc7e580-9012-11e8-9c06-010c74b29e42.png)
