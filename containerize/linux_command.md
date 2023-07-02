# Encoding / Decoding

## base64 encoding / decoding
"echo -n" removes the trailing newline character.
```
echo -n [text_to_encode]| base64
echo -n [text_to_decode]| base64 --decode
```