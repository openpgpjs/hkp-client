# HKP Client

This libary implements a client for the OpenPGP HTTP Keyserver Protocol (HKP)
in order to lookup and upload keys on standard public key servers.

## Examples

### Lookup public key on HKP server

```js
import HKP from '@openpgp/hkp-client';
import { readKey } from 'openpgp';

(async () => {
  var hkp = new HKP(); // Defaults to https://keyserver.ubuntu.com, or pass another keyserver URL as a string

  let publicKeyArmored = await hkp.lookup({
      query: 'alice@example.com'
  });
  let publicKey = await readKey({ armoredKey: publicKeyArmored });
})();
```

### Upload public key to HKP server

```js
import HKP from '@openpgp/hkp-client';
(async () => {
  var hkp = new HKP('https://pgp.mit.edu');

  var publicKeyArmored = `-----BEGIN PGP PUBLIC KEY BLOCK-----
...
-----END PGP PUBLIC KEY BLOCK-----`;

  await hkp.upload(publicKeyArmored);
})();
```
