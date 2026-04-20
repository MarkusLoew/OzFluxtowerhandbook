# Data transfer

Options when using a Campbell Scientific data logger.

## Direct download from data logger

Via serial cable (serial or USB) as shown on the communication page. Requires direct access to the data logger.

## Loggernet / PC400 internal data-transfer

-   Manual download
-   Scheduled collection

## ftp

Be aware of the security implications when using the outdated, not-encrypted ftp protocol! ftp transmits its password during each connection in clear text. In CRBAsic programs for some loggers, the password is also stored as plain text. Some universities do not allow ftp servers on their network! However, for many older or "smaller" data logger models, ftp is the only available file transfer protocol, e.g. CR310, CR1000, CR3000. But some of these loggers also provide a http server as alternative. The security risk is somewhat mitigated when the ftp connection takes place within a trusted network or VPN like TERN OpenVPN.

### ftp upload to a server

-   use CRBasic `FTPClient()` command to send data from the logger to a server
-   set up in a SlowSequence as not to interrupt the measurements

### ftp download from the logger

-   Campbell Scientific data loggers have an optional, built-in ftp server that allows files to be downloaded directly from the logger.
-   use any ftp computer software to download files from the logger.

## sftp (ssh)

Insteas of ftp use the sftp: sftp (SSH File Transfer Protocol) is a secure alternative to ftp. It encrypts both the command and data channels, providing confidentiality and integrity. Passwords are not necessarily stored in the CRBasic program. Instead, the sftp client uses private and public keys to authenticate. The keys are stored in the memory of the data logger. An introduction to setting up keys on the logger is available [from Campbell Scientific: "How to Generate SFTP Keys Easily"](https://www.campbellsci.com.au/blog/generate-sftp-keys-easily). In the program, the upload is done with `FTPClient()`, see example below.

# http