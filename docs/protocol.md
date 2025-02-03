The protocol currently used to transfer data between the LoRa RYLR896 radio on the Weather Station to an identical radio on the broker uses ASCII to encode plain-text data.

## Protocol

Note that the protocol used to communicate over the radio is NOT the binary protocol described in the wiki, but is a simple ASCII string. 

String: `T00.00|H00.00|P00.00|R<0 or 1>|L<0,1,2>`

There is more data transmitted over the LoRa radio, but the string above is what the payload looks like.

!!! info "Future Protocol"

    In the future, the binary protocol defined elsewhere in this documentation will be used for transferring environmental data.

## Future
In the future, another protocol that uses binary support would be better for throughput as the same data can be encoded in less bits sent.