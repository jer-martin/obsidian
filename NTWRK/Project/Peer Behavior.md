- ### Handshake and Bitfield
	- Suppose that peer A tries to make a TCP connection to peer B. 
		- *Here we are describing only peer A's behavior, but peer B should mirror it.*
	- After TCP connection is established, peer A sends a handshake message to peer B
		- It also receives a handshake message from peer B and checks whether peer B is the right neighbor
		- To do this, it checks the handshake header and the peer ID
	- After handshaking, peer A sends a 'bitfield' message to let peer B know which file pieces it has
		- Peer B will also send a 'bitfield' message to peer A, unless it has no pieces
	- If peer A receives a bitfield message from peer B and it finds out peer B has pieces that it doesn't have, peer A will send 'interested' message to peer B. Otherwise, it sends 'not interested'


- ### Choke and Unchoke
	- 