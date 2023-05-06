import random
import socket
import string
import argparse

def msg(text : str):
    print(text)

class Client():
    def __init__(self, serv_host : str, serv_port : int) -> None:
        self.host = serv_host
        self.port = serv_port

    def _create_cli_process(self):
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        server_adress = (self.host, self.port)
        sock.connect(server_adress)
        return sock

    def process_client(self, client_sock : socket.socket):
        data = self._generate_str(20000000)
        client_sock.sendall(data)
        msg(f'Send at server {len(data)} bytes')
        msg(f'Data is {data}')

    def _generate_str(self, len_str : int):
        letters = string.ascii_lowercase
        result_str = ''.join(random.choice(letters) for i in range(len_str))
        return bytes(result_str, "ascii")

def main():
    parser = argparse.ArgumentParser()
    parser.add_argument('-host', required= True)
    parser.add_argument('-port', required= True, type = int)
    args = parser.parse_args()
    host =args.host
    port =args.port
    client = Client(host, port)
    client_sock = client._create_cli_process()
    client.process_client(client_sock)

if __name__ == "__main__":
    main()