# @omegion1npm/qui-iste-quis

JavaScript library of crypto standards.

## Discontinued

Active development of CryptoJS has been discontinued. This library is no longer maintained.

Nowadays, NodeJS and modern browsers have a native `Crypto` module. The latest version of CryptoJS already uses the native Crypto module for random number generation, since `Math.random()` is not crypto-safe. Further development of CryptoJS would result in it only being a wrapper of native Crypto. Therefore, development and maintenance has been discontinued, it is time to go for the native `crypto` module.

## Node.js (Install)

Requirements:

- Node.js
- npm (Node.js package manager)

```bash
npm install @omegion1npm/qui-iste-quis
```

### Usage

ES6 import for typical API call signing use case:

```javascript
import sha256 from '@omegion1npm/qui-iste-quis/sha256';
import hmacSHA512 from '@omegion1npm/qui-iste-quis/hmac-sha512';
import Base64 from '@omegion1npm/qui-iste-quis/enc-base64';

const message, nonce, path, privateKey; // ...
const hashDigest = sha256(nonce + message);
const hmacDigest = Base64.stringify(hmacSHA512(path + hashDigest, privateKey));
```

Modular include:

```javascript
var AES = require("@omegion1npm/qui-iste-quis/aes");
var SHA256 = require("@omegion1npm/qui-iste-quis/sha256");
...
console.log(SHA256("Message"));
```

Including all libraries, for access to extra methods:

```javascript
var CryptoJS = require("@omegion1npm/qui-iste-quis");
console.log(CryptoJS.HmacSHA1("Message", "Key"));
```

## Client (browser)

Requirements:

- Node.js
- Bower (package manager for frontend)

```bash
bower install @omegion1npm/qui-iste-quis
```

### Usage

Modular include:

```javascript
require.config({
    packages: [
        {
            name: '@omegion1npm/qui-iste-quis',
            location: 'path-to/bower_components/@omegion1npm/qui-iste-quis',
            main: 'index'
        }
    ]
});

require(["@omegion1npm/qui-iste-quis/aes", "@omegion1npm/qui-iste-quis/sha256"], function (AES, SHA256) {
    console.log(SHA256("Message"));
});
```

Including all libraries, for access to extra methods:

```javascript
// Above-mentioned will work or use this simple form
require.config({
    paths: {
        '@omegion1npm/qui-iste-quis': 'path-to/bower_components/@omegion1npm/qui-iste-quis/@omegion1npm/qui-iste-quis'
    }
});

require(["@omegion1npm/qui-iste-quis"], function (CryptoJS) {
    console.log(CryptoJS.HmacSHA1("Message", "Key"));
});
```

### Usage without RequireJS

```html
<script type="text/javascript" src="path-to/bower_components/@omegion1npm/qui-iste-quis/@omegion1npm/qui-iste-quis.js"></script>
<script type="text/javascript">
    var encrypted = CryptoJS.AES(...);
    var encrypted = CryptoJS.SHA256(...);
</script>
```

## API

See: https://cryptojs.gitbook.io/docs/

### AES Encryption

#### Plain text encryption

```javascript
var CryptoJS = require("@omegion1npm/qui-iste-quis");

// Encrypt
var ciphertext = CryptoJS.AES.encrypt('my message', 'secret key 123').toString();

// Decrypt
var bytes  = CryptoJS.AES.decrypt(ciphertext, 'secret key 123');
var originalText = bytes.toString(CryptoJS.enc.Utf8);

console.log(originalText); // 'my message'
```

#### Object encryption

```javascript
var CryptoJS = require("@omegion1npm/qui-iste-quis");

var data = [{id: 1}, {id: 2}]

// Encrypt
var ciphertext = CryptoJS.AES.encrypt(JSON.stringify(data), 'secret key 123').toString();

// Decrypt
var bytes  = CryptoJS.AES.decrypt(ciphertext, 'secret key 123');
var decryptedData = JSON.parse(bytes.toString(CryptoJS.enc.Utf8));

console.log(decryptedData); // [{id: 1}, {id: 2}]
```

### List of modules


- ```@omegion1npm/qui-iste-quis/core```
- ```@omegion1npm/qui-iste-quis/x64-core```
- ```@omegion1npm/qui-iste-quis/lib-typedarrays```

---

- ```@omegion1npm/qui-iste-quis/md5```
- ```@omegion1npm/qui-iste-quis/sha1```
- ```@omegion1npm/qui-iste-quis/sha256```
- ```@omegion1npm/qui-iste-quis/sha224```
- ```@omegion1npm/qui-iste-quis/sha512```
- ```@omegion1npm/qui-iste-quis/sha384```
- ```@omegion1npm/qui-iste-quis/sha3```
- ```@omegion1npm/qui-iste-quis/ripemd160```

---

- ```@omegion1npm/qui-iste-quis/hmac-md5```
- ```@omegion1npm/qui-iste-quis/hmac-sha1```
- ```@omegion1npm/qui-iste-quis/hmac-sha256```
- ```@omegion1npm/qui-iste-quis/hmac-sha224```
- ```@omegion1npm/qui-iste-quis/hmac-sha512```
- ```@omegion1npm/qui-iste-quis/hmac-sha384```
- ```@omegion1npm/qui-iste-quis/hmac-sha3```
- ```@omegion1npm/qui-iste-quis/hmac-ripemd160```

---

- ```@omegion1npm/qui-iste-quis/pbkdf2```

---

- ```@omegion1npm/qui-iste-quis/aes```
- ```@omegion1npm/qui-iste-quis/tripledes```
- ```@omegion1npm/qui-iste-quis/rc4```
- ```@omegion1npm/qui-iste-quis/rabbit```
- ```@omegion1npm/qui-iste-quis/rabbit-legacy```
- ```@omegion1npm/qui-iste-quis/evpkdf```

---

- ```@omegion1npm/qui-iste-quis/format-openssl```
- ```@omegion1npm/qui-iste-quis/format-hex```

---

- ```@omegion1npm/qui-iste-quis/enc-latin1```
- ```@omegion1npm/qui-iste-quis/enc-utf8```
- ```@omegion1npm/qui-iste-quis/enc-hex```
- ```@omegion1npm/qui-iste-quis/enc-utf16```
- ```@omegion1npm/qui-iste-quis/enc-base64```

---

- ```@omegion1npm/qui-iste-quis/mode-cfb```
- ```@omegion1npm/qui-iste-quis/mode-ctr```
- ```@omegion1npm/qui-iste-quis/mode-ctr-gladman```
- ```@omegion1npm/qui-iste-quis/mode-ofb```
- ```@omegion1npm/qui-iste-quis/mode-ecb```

---

- ```@omegion1npm/qui-iste-quis/pad-pkcs7```
- ```@omegion1npm/qui-iste-quis/pad-ansix923```
- ```@omegion1npm/qui-iste-quis/pad-iso10126```
- ```@omegion1npm/qui-iste-quis/pad-iso97971```
- ```@omegion1npm/qui-iste-quis/pad-zeropadding```
- ```@omegion1npm/qui-iste-quis/pad-nopadding```


## Release notes

### 4.2.0

Change default hash algorithm and iteration's for PBKDF2 to prevent weak security by using the default configuration.

Custom KDF Hasher

Blowfish support

### 4.1.1

Fix module order in bundled release.

Include the browser field in the released package.json.

### 4.1.0

Added url safe variant of base64 encoding. [357](https://github.com/omegion1npm/qui-iste-quis/pull/357)

Avoid webpack to add crypto-browser package. [364](https://github.com/omegion1npm/qui-iste-quis/pull/364)

### 4.0.0

This is an update including breaking changes for some environments.

In this version `Math.random()` has been replaced by the random methods of the native crypto module.

For this reason CryptoJS might not run in some JavaScript environments without native crypto module. Such as IE 10 or before or React Native.

### 3.3.0

Rollback, `3.3.0` is the same as `3.1.9-1`.

The move of using native secure crypto module will be shifted to a new `4.x.x` version. As it is a breaking change the impact is too big for a minor release.

### 3.2.1

The usage of the native crypto module has been fixed. The import and access of the native crypto module has been improved.

### 3.2.0

In this version `Math.random()` has been replaced by the random methods of the native crypto module.

For this reason CryptoJS might does not run in some JavaScript environments without native crypto module. Such as IE 10 or before.

If it's absolute required to run CryptoJS in such an environment, stay with `3.1.x` version. Encrypting and decrypting stays compatible. But keep in mind `3.1.x` versions still use `Math.random()` which is cryptographically not secure, as it's not random enough. 

This version came along with `CRITICAL` `BUG`. 

DO NOT USE THIS VERSION! Please, go for a newer version!

### 3.1.x

The `3.1.x` are based on the original CryptoJS, wrapped in CommonJS modules.


