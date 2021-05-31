# Crockford's Base32
## Install
`npm i --save @darkwolf/base32crockford`
## Usage
```javascript
// ECMAScript
import Base32Crockford from '@darkwolf/base32crockford'
// CommonJS
const Base32Crockford = require('@darkwolf/base32crockford')

// Number Encoding
const integer = Number.MAX_SAFE_INTEGER // => 9007199254740991
const encodedInt = Base32Crockford.encodeInt(integer) // => '7ZZZZZZZZZZ'
const decodedInt = Base32Crockford.decodeInt(encodedInt) // => 9007199254740991

const negativeInteger = -integer // => -9007199254740991
const encodedNegativeInt = Base32Crockford.encodeInt(negativeInteger) // => '-7ZZZZZZZZZZ'
const decodedNegativeInt = Base32Crockford.decodeInt(encodedNegativeInt) // => -9007199254740991

// BigInt Encoding
const bigInt = BigInt(Number.MAX_VALUE) // => 179769313486231570814527423731704356798070567525844996598917476803157260780028538760589558632766878171540458953514382464234321326889464182768467546703537516986049910576551282076245490090389328944075868508455133942304583236903222948165808559332123348274797826204144723168738177180919299881250404026184124858368n
const encodedBigInt = Base32Crockford.encodeBigInt(bigInt) // => 'FZZZZZZZZZY00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
const decodedBigInt = Base32Crockford.decodeBigInt(encodedBigInt) // => 179769313486231570814527423731704356798070567525844996598917476803157260780028538760589558632766878171540458953514382464234321326889464182768467546703537516986049910576551282076245490090389328944075868508455133942304583236903222948165808559332123348274797826204144723168738177180919299881250404026184124858368n

const negativeBigInt = -bigInt // => -179769313486231570814527423731704356798070567525844996598917476803157260780028538760589558632766878171540458953514382464234321326889464182768467546703537516986049910576551282076245490090389328944075868508455133942304583236903222948165808559332123348274797826204144723168738177180919299881250404026184124858368n
const encodedNegativeBigInt = Base32Crockford.encodeBigInt(negativeBigInt) // => '-FZZZZZZZZZY00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
const decodedNegativeBigInt = Base32Crockford.decodeBigInt(encodedNegativeBigInt) // => -179769313486231570814527423731704356798070567525844996598917476803157260780028538760589558632766878171540458953514382464234321326889464182768467546703537516986049910576551282076245490090389328944075868508455133942304583236903222948165808559332123348274797826204144723168738177180919299881250404026184124858368n

// Text Encoding
const text = 'Ave, Darkwolf!'
const encodedText = Base32Crockford.encodeText(text) // => '85V6AB108HGQ4TVQDXP6C88'
const decodedText = Base32Crockford.decodeText(encodedText) // => 'Ave, Darkwolf!'

const emojis = '🐺🐺🐺'
const encodedEmojis = Base32Crockford.encodeText(emojis) // => 'Y2FS1EQGKY8BNW4ZJ2X0'
const decodedEmojis = Base32Crockford.decodeText(encodedEmojis) // => '🐺🐺🐺'

// Buffer Encoding
const buffer = Uint8Array.of(0x00, 0x02, 0x04, 0x08, 0x0f, 0x1f, 0x3f, 0x7f, 0xff) // => <Uint8Array 00 02 04 08 0f 1f 3f 7f ff>
const encodedBuffer = Base32Crockford.encode(buffer) // => <Uint8Array 30 30 31 30 38 32 30 46 33 57 5a 51 5a 5a 52>
const decodedBuffer = Base32Crockford.decode(encodedBuffer) // => <Uint8Array 00 02 04 08 0f 1f 3f 7f ff>

const encodedBufferToString = Base32Crockford.encodeToString(buffer) // => '0010820F3WZQZZR'
const decodedBufferFromString = Base32Crockford.decodeFromString(encodedBufferToString) // => <Uint8Array 00 02 04 08 0f 1f 3f 7f ff>

// Custom Alphabet
const base32crockford = new Base32Crockford('ABCDEFGHJKMNPQRSTVWXYZ0123456789')

const encInt = base32Crockford.encodeInt(integer) // => 'H9999999999'
const decInt = base32Crockford.decodeInt(encInt) // => 9007199254740991

const encNegativeInt = base32Crockford.encodeInt(negativeInteger) // => '-H9999999999'
const decNegativeInt = base32Crockford.decodeInt(encNegativeInt) // => -9007199254740991

const encBigInt = base32Crockford.encodeBigInt(bigInt) // 'S9999999998AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'
const decBigInt = base32Crockford.decodeBigInt(encBigInt) // => 179769313486231570814527423731704356798070567525844996598917476803157260780028538760589558632766878171540458953514382464234321326889464182768467546703537516986049910576551282076245490090389328944075868508455133942304583236903222948165808559332123348274797826204144723168738177180919299881250404026184124858368n

const encNegativeBigInt = base32Crockford.encodeBigInt(negativeBigInt) // => '-S9999999998AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'
const decNegativeBigInt = base32Crockford.decodeBigInt(encNegativeBigInt) // => -179769313486231570814527423731704356798070567525844996598917476803157260780028538760589558632766878171540458953514382464234321326889464182768467546703537516986049910576551282076245490090389328944075868508455133942304583236903222948165808559332123348274797826204144723168738177180919299881250404026184124858368n

const encText = base32Crockford.encodeText(text) // => 'JF5GMNBAJVT1E451Q70GPJJ'
const decText = base32Crockford.decodeText(encText) // => 'Ave, Darkwolf!'

const encEmojis = base32Crockford.encodeText(emojis) // => '8CS3BR1TX8JNZ6E9WC7A'
const decEmojis = base32Crockford.decodeText(encEmojis) // => '🐺🐺🐺'

const encBuffer = base32Crockford.encode(buffer) // => <Uint8Array 41 41 42 41 4a 43 41 53 44 36 39 31 39 39 32>
const decBuffer = base32Crockford.decode(encBuffer) // => <Uint8Array 00 02 04 08 0f 1f 3f 7f ff>

const encBufferToString = base32Crockford.encodeToString(buffer) // => 'AABAJCASD691992'
const decBufferFromString = base32Crockford.decodeFromString(encBufferToString) // => <Uint8Array 00 02 04 08 0f 1f 3f 7f ff>
```
## [API Documentation](https://github.com/Darkwolf/node-base32crockford/blob/master/docs/API.md)
## Contact Me
#### GitHub: [@PavelWolfDark](https://github.com/PavelWolfDark)
#### Telegram: [@PavelWolfDark](https://t.me/PavelWolfDark)
#### Email: [PavelWolfDark@gmail.com](mailto:PavelWolfDark@gmail.com)
