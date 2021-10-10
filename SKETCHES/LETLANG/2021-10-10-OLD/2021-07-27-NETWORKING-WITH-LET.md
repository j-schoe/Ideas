# Networking With Let

Afaik there are essentially two different types
of networking protocols:

| Packet-switched   | Circuit-switched |
|:----------------- |:---------------- |
| Datagram-based    | Stream-based     |
| Ethernet, IP, UDP | TCP, Quic        |

Its hard to emulate one of those over the other.
> Is it?

## Addresses

Based on [multiaddresses](https://github.com/multiformats/multiaddr)!

```
Address("/ip4/10.20.30.40/tcp/8080")
Address("/dns/example.com/udp/1234/quic")

Address(0x<<binary-multiaddr>>)

Address("tcp4://example.net:2020")
```

## Sockets

> String literals are implicitly converted to
addresses.

```
let s = StreamSocket.Open("/tcp/1234")
let p = PacketSocket.Open("/udp/4321")
```

Omitting the network part of the address is
equivalent to `/ip4/0.0.0.0` or `/ip6/::`,
which means "this host on this network".
Just in a protocol agnostic way.

```
s.Dial("/ip4/10.20.30.40/")
s.Listen()
```

## I/O

### Blocking I/O

```
let str: DuplexStream(Byte) = s.Dial(...).Apply()
str.Put(Encoding."UTF-8".Encode("Hello World\n"))
str.Close()
```

### Akka-style declarative I/O

```
let dep: DuplexEndpoint(Byte) = s.Dial(...)
let src: Source(Byte) = "Hello World\n" >> Encoding."UTF-8".Encode
let snk: Sink(Byte) = Sink.Void

run(src >> dep >> snk)
```

## Socket vs. Socket

```
type LocalStreamSocket = trait {
  let Local: Address

  fun Dial(let Remote: Address): BoundSocket

  fun Listen(): BoundSocket

  fun Listen(let Handler: BoundSocket -> Unit): Unit
}

type BoundStreamSocket = trait {
  extends DuplexEndpoint(Byte)

  let Local: Address

  let Remote: Address
}

type LocalPacketSocket = trait {
  let Local: Address

  let Dial(let Remote: Address): OutboundPacketSocket

  let Listen(): InboundPacketSocket

  let Listen(let Handler: InboundPacketSocket -> Unit): Unit
}

type OutboundPacketSocket = trait {
  extends Sink(Byte)

  let Local: Address

  let Remote: Address
}

type InboundPacketSocket = trait {
  extends Source(Byte)

  let Local: Address

  let Remote: Address
}

```














