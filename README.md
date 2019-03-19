# byakugan
Simple, encrypted peer discovery library. For my own educational purposes

## About the Name
Just let me have my fun, to be honest.

## Model
There is one central, trusted server, and an infinite amount of peers,
which cannot be trusted without verification from the server.

This system has just a few goals:
* Allow peers to know how many other peers are active
* Allow peers to obtain the IP and port of any other peer
* Provide peers the information necessary to differentiate between trusted peers,
and random computers which might be adversarial
  * When peer A wants to connect to peer B, peer A generates a public/private key pair,
  and the server also generates a public/private key
  pair. The server then sends both of its keys, as well as peer A's IP address (encrypted by means
  of peer A's public key) to peer B, and sends peer A the IP and port of peer B, as well as the
  server's public key.
  peer A.
  * Peer A then opens a connection to peer B, and sends the key it received from the server.
  * Peer B uses this most recent key to decrypt peer A's IP, and compares it to the actual IP
  that is contacting it. If these do not match, the connection is rejected.
  * Finally, peer B validates the keys sent from the server, as well.
