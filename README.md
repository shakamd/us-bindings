us-bindings
===========

Various bindings for [`us`](https://github.com/lukechampine/us). Highly experimental.

## Installation

### iOS

```
go get -u lukechampine.com/us-bindings/gomobile
go get golang.org/x/mobile/cmd/gomobile
gomobile bind -target=ios lukechampine.com/us-bindings/gomobile
```

This will produce a framework, `Us.framework`, which you can import into Xcode.

### Android

See https://github.com/golang/go/wiki/Mobile#building-and-deploying-to-android-1


## Forming Contracts

The bindings accept contracts in the form of a 96-byte array, consisting of the
host public key, file contract ID, and renter secret key. The easiest way to
acquire such a contract is via [`user`](https://github.com/lukechampine/user):

```
user form [host key] 100SC 1000 example.contract
xxd -ps -s 12 -l 96 example.contract | tr -d '\n'
```

This will print the contract as a 192-byte hex string. You can convert this to a
QR code using a local program/library or any number of online generator
services.

It is also possible to convert `siad` contracts to this format, but it's a
little trickier. I will provide a script to perform the conversion upon request.
