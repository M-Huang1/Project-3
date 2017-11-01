Project 3 
Marshall White and Zhao Huang

For project 3, our high level approach was using culmative ACKS and slow start with a set window recovery size.
Our window size initially starts at 10 and increments as the sender recieves ACKs from the reciever.
When a message is dropped or transmitted out of order, the window size drops to 5.
The reciever always sends a culmative ACK meaning it sends the sequence of the last message that was recieved
in order and buffer any messages that are out order until all the ordered pieces arrive at the reciever.
This approach accounts for both dropped and reordered packets because the window will only account for ordered packets,
and all other packets are buffered into reciever until the right packet is sent to the reciever, although dropped packets
cause a big time discrepancy because of the return to a window size of 5.
Many of the problems we ran into were because of implmentation bugs that were overlooked or that we didn't see until 
we saw the logs of the sender and reciever. We wanted to start with SACK, but we eventually came to the conclusion that
Cumulative ACK did the job just fine.
We tested our code by running the run file and changing the properties of the server for drops and reordering as well as size
with the netsim command.


 