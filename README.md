# Simple SOCKET Client|Server App

**User `socket` module for implementation**

For more `https://docs.python.org/3/library/socket.html`

## Server

1. Implement Server application that receives data and send it back to sender
2. Append Server configuration (listening host and port). Configuration MUST NOT be hardcoded.
3. Implement Server as separate class
4. Streaming TCP data MUST be processed (count received data len, should be received all data)
5. On `socket.recv(data_len)` `data_len` could not be more than `4096`

## Client

1. Implement Client application that sends data to server, 
then receives data from server and prints it on console
2. Server addr (host and port) MUST NOT be hardcoded.
3. Implement Client as separate class
4. For data sending on client `sendall` function could be used
