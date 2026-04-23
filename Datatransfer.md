# Data transfer

Options when using a Campbell Scientific data logger.

## Direct download from data logger

The simplest form of data transfer is the getting the data straight off the memory card of the logger. Either via cable or by removing the memory card. Via serial cable (serial or USB) as shown on the [communication page](./Communication.html). Requires direct access to the data logger.

## Sneaker net

*"Never underestimate the bandwidth of a station wagon full of tapes hurtling down the highway."* — Andrew S. Tanenbaum (1989)

It can be faster to go to the tower, copy the data off the logger, and then transport it back to the office instead of transferring the data via the internet. Many Campbell Scientific data loggers have removable memory cards that make this process straightforward. IE. CF cards for the CR1000, CR3000, etc or micro-SD cards for the CR6, CR1000x data loggers.

-   [Industrial-grade microSD card (RS Online)](https://au.rs-online.com/web/p/sd-cards/0278580) [ATP Industrial Grade 16 GB microSD Card, Class 10, UHS 1](https://au.rs-online.com/web/p/sd-cards/0278580)

![Compact Flash card and adaptors for Campbell Scientific data loggers. A CR3000 (or CR1000) can be equipped with CF card adaptors: Either the NL115 ethernet/CF card adaptor, or the CFM100 CF card adaptor. 2 GB CF card and micro SD (for CR6 or CR1000x(e) data loggers) card shown (Markus Loew).](images/communication/Memory_cards_20260423_052200591.jpg)

## Loggernet / PC400 internal data-transfer

-   Manual download via *Loggernet Connect*
-   Scheduled collection

## ftp

Data can be transmitted from the data logger to a server via the file transfer protocol. The data logger acts as a ftp client.

Be aware of the security implications when using the outdated, not-encrypted ftp protocol! ftp transmits its password during each connection in clear text. In CRBAsic programs for some loggers, the password is also stored as plain text. Some universities do not allow ftp servers on their network! However, for many older or "smaller" data logger models, ftp is the only available file transfer protocol, e.g. CR310, CR1000, CR3000. But some of these loggers also provide a http server as alternative (see below). The security risk is somewhat mitigated when the ftp connection takes place within a trusted network or [VPN](./TERNOpenVPN.html) like TERN OpenVPN.

The CRBasic command for ftp upload is [`FTPClient()`](https://help.campbellsci.com/crbasic/cr1000x/#Instructions/ftpclient.htm). With `PutGetoption 9` for a "passive" ftp server, which is the most common type an and appending to/creating file if it does not exist.

### ftp upload to a server

-   use CRBasic `FTPClient()` command to send data from the logger to a server
-   set up in a SlowSequence as not to interrupt the measurements

#### Example CRBasic program for ftp upload

`'server information for data upload`

`Const server = "my.server.here.au"`

`Const FTP_Port = 4221`

`Const User = "logger"`

`Const Pass = ""`

`Const Folder = "/destination/ftp/towername/"`

\[...\]

`' Create public variable to keep track of data transfer sucess / status`

`' must exist for each table`

`Upload_status_TERNflux Public`

\[...\]

`' If the filename of the server requires a timestamp`

`Public TStamp As String * 16 ' create a 30 min timestamp for ts_data`

\[...\]

`SlowSequence`

`Scan (OUTPUT_INTERVAL, Min, 5, 0)`

`Upload_status_TERNflux = FTPClient(server, User, Pass, "TERNFlux", "Towername/TERNFlux.dat", 9, 0, 0, 0, -1008)`

`' to create a filename on the server that includes a timestamp:`

`TStamp = Public.Timestamp(5, 1)`

`'e.g. 30 min timestamp:`

`TStamp = Left(TStamp, 16)`

`' building the filename on the fly to include current timestamp`

`Upload_status_mytable = FTPClient(Server, User, Pass, "Mytable", Folder & "Towername" & TStamp & "_30_min.dat", 9, 0, 0, Min, -1008)`

`NextScan`

`EndSequence`

### ftp download from the logger

-   Campbell Scientific data loggers have an optional, built-in *ftp server* that allows files to be downloaded directly from the logger.
-   use any ftp computer software to download files from the logger.

## sftp (ssh)

*sftp* (SSH File Transfer Protocol) is a secure and more modern alternative to ftp. It encrypts both the command and data channels, providing confidentiality and integrity. Passwords are not necessarily stored in the CRBasic program. Instead, the sftp client uses private and public keys to authenticate. The keys are stored in the memory of the data logger. An introduction to setting up keys on the logger is available [from Campbell Scientific: "How to Generate SFTP Keys Easily"](https://www.campbellsci.com.au/blog/generate-sftp-keys-easily). In the program, the upload is done with `FTPClient()`, see example below.

# http