## lib-encryption
---
simple encryption class for node apps, allows setting app secret & set purpose of encryption, inspired from adonis encryption feature

## Quick Start

```ts
// Create Static Encryption constant
// src/lib/Encryption.ts
import { default as AppEncryption } from 'lib-encryption';
const Encryption = new AppEncryption({ secret: process.env.APP_SECRET })
export default Encryption;

// usage
// src/app.ts or any other ts to use

import Encryption from './lib/Encryption';

// encrypt payload with a expiry date & purpose which acts like a salt, decrypting will require the purpose to return the encrypted object, otherwise null
const token = Encryption.encrypt({ userId: "<some id>" }, Date.now() + 1000 * 60 * 60, "emailVerify");

// some user <> server things

// server handles payload
const payload = Encryption.decrypt(token, "emailVerify");

```
