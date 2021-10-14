# IDFY-Json-RPC

## Methods

The idea is that on every invocation a pop-up is
displayed to the user where they have to accept
or deny the operation.

### Intoduce

Intoduces a new client to the wallet.
The client provides a list of things they might
have to do in the future.

### Get-Secret

> Unsafe!

Returns one of the private keys associated
with the did. Obviously a bad idea!

### Sign-Blob / Sign-Jose / Sign-Cose

> Unsafe!

Signes arbitrary data provided by the client.
Thus the data can be everything, everything can
be asserted by the client when allowed.
Clients should use Claim-Credential instead!

### Claim-Credential

> Questionable!

Issues a verifiable credential in the name of the
user to the client. The subject of the vc could be
associated with a description which is displayed
to the user.



