- P2P File sharing software
	- similar to bittorrent

*Java or C/C++*

The protocol consists of a [handshake](Peer%20Behavior.md) followed by a never ending stream of length-prefixed messages. 

The handshake is a message sent between the peers when a connection is established. It consists of three parts:
- The header
	- An 18 byte string
- Zero bits
	- 10 zero bits
- Peer ID
	- 4 byte integer representation

After handshaking, each peer can send a stream of actual messages. Each message consists of:
- Message length field
	- 4 bytes
	- Specifies the length of the message in bytes
- Message type field
	- 1 byte
	- Specifies the [Message Type ](Message%20Type%20Overview.md). There are 8 types:
 <div style="overflow-x: auto; text-align: center;">
<table border="1" style="width: 75%; border-collapse: collapse; margin-left: auto; margin-right: auto">
<thead>
<tr>
<th>message type</th>
<th>value</th>

</tr>
</thead>
<tbody>
<tr>
<td>choke</td>
<td>0</td>
</tr>
<tr>
<td>unchoke</td>
<td>1</td>
</tr>
<tr>
<td>interested</td>
<td>2</td>
</tr>
<tr>
<td>not interested</td>
<td>3</td>
</tr>
<tr>
<td>have</td>
<td>4</td>
</tr>
<tr>
<td>bitfield</td>
<td>5</td>
</tr>
<tr>
<td>request</td>
<td>6</td>
</tr>
<tr>
<td>piece</td>
<td>7</td>
</tr>
<!-- Add more rows as needed -->
</tbody>
</table>
</div>
- Message payload
	- Variable size



