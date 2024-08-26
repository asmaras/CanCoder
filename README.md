# CanCoder
Decoding and encoding of CAN bus messages.
\
This coder is able to encode messages that have unkown/undocumented fields by encoding the known fields and adding non-decoded data from a previous decode. If no decode was performed yet the non-decoded data is filled to the best of knowledge (from analysing CAN bus message logs).

Functions for logging raw messages (hexadecimal) or message contents are also available.

Currently supported is a subset of the messages for the BMW Mini R60. There may be overlap with other BMW vehicles.

Description from header file:
```
 * When decoding, only the relevant fields are decoded from the data. All non-decoded
 * data however is stored seperately for each identifier. For each identifier there is
 * a struct member holding it's data.
 * This way, encoding will always produce a complete message containing both decoded
 * and non-decoded data based on the latest decode for that identifier. If no decode
 * was performed yet the non-decoded data is filled to the best of knowledge.
 * For example:
 * You decode a message for identifier x, containing fields a and b and undecoded
 * bytes 4 and 5. Then you decode and encode some messages for other identifiers and
 * then you decide to encode a message for identifier x, but you only change field a.
 * What happens is that field b will be encoded as it was decoded previously and bytes
 * 4 and 5 that were not decoded will now still be included, resulting in a complete
 * message.
```
