The Bafang display protocol is a request/response protocol where the Display 
sends the requests and the controller responds. It utilizes a trailing checksum  
and is full of inconsistencies.


## Serial Protocol

Rules:
* Read requests starts with 0x11
* Write requests starts with 0x16

The next byte is an opcode for the type of operation.














