import socket
import argparse

def msg(text : str):
    print(text)

class Server():
    def __init__(self, host : str,port : int) -> None:
        self.host = host
        self.port = port

    def start_server(self):
        sock = self._create_server_sock()
        #create new socket
        msg(f"Created server sock on {self.host}:{self.port}")
        msg(f'Sock is {sock}')
        while True:
            self._accept_and_process_cli(sock)

    def _accept_and_process_cli(self, sock : socket.socket):
        #Accept new client connect
        #cli_sock - new client socket
        #cli_addr - client addr
        msg('Accepting new client connection ...')
        cli_sock, cli_addr = sock.accept()
        msg(f"Accepted client: {cli_addr}")
        #work at new client connection
        msg(cli_sock)
        self._cli_process(cli_sock)

    def _cli_convert_bytes(self, data : bytes):
        data_str = data.decode('ascii')
        return data_str

    def _cli_process(self, cli_sock : socket.socket):
        while True:
            data = cli_sock.recv(4096)
            if not data :
                break
            else:
                msg(self._cli_convert_bytes(data))

    def _create_server_sock(self):
        #create sock for server
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        # Binding created socket in addr (host, port)
        addr = (self.host,self.port)
        sock.bind(addr)
        # Listening on bound sock
        sock.listen()
        return sock

def main():
    parser = argparse.ArgumentParser()
    parser.add_argument('-host', required= True)
    parser.add_argument('-port', required= True, type=int)
    args = parser.parse_args()
    host = args.host
    port = args.port
    serv = Server(host, port)
    serv.start_server()
if __name__ == '__main__':
    main()
