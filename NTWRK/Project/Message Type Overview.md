- Choke
- Unchoke
- Interested
- Not Interested
	- These messages have no payload.

- Have
	- 'Have' messages have a payload that contains a 4-byte piece index field

- Bitfield
	- 'Bitfield' messages are only sent as the first message, immediately after connection is established
	- It has a *bitfield* as it's payload
		- A *bitfield* is an array of bits where each bit represents whether the peer has the corresponding piece or not
		- The first byte of the bitfield corresponds to piece indices 0-7 from high bit to low bit
		- The next corresponds to piece indices 8 - 15, etc.
		- Spare bits at the end are set to zero
	- Peers that do not have anything may skip a 'bitfield' message

- Request
	- 'Request' messages have a payload which consists of a 4-byte piece index field
	- *NOTE:* this 'request' message payload is different than BitTorrent's. We do not divide the pieces into smaller subpieces.

- Piece
	- 'Piece' messages have a payload which consists of a 4-byte piece index field and the content of the piece