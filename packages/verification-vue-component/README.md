# @certifaction/verification-vue-component

[![npm][npm]][npm-url]
[![lerna][lerna]][lerna-url]

The verification vue-component enables you to easily integrate the Certifaction Verification Tool into your VueJS project.

## Table of contents

* [Requirements](#requirements)
* [Install](#install)
    * [As NPM package](#as-npm-package)
    * [Load locales](#load-locales)
    * [Load stylesheet](#load-stylesheet)
* [Usage](#usage)
* [Props](#props)
    * [demo](#demo)
    * [enableClaims](#enableClaims)
    * [providerUrl](#providerUrl)
    * [legacyContractAddress](#legacyContractAddress)
    * [legacyContractFallbackAddresses](#legacyContractFallbackAddresses)
    * [claimContractAddress](#claimContractAddress)
    * [acceptedIssuerKey](#acceptedIssuerKey)
    * [certifactionApiUrl](#certifactionApiUrl)
    * [offchainVerifier](#offchainVerifier)
* [License](#license)

## Requirements

* [Vue.js](https://vuejs.org/) (^2.6)
* [Vue I18n](https://kazupon.github.io/vue-i18n/) (^8.21)

## Install

### As NPM package

```shell script
npm install @certifaction/verification-vue-component

# or if using yarn
yarn add @certifaction/verification-vue-component
```

## Usage

### ES6

```js
import CertifactionVerification from '@certifaction/verification-vue-component'

new Vue({
    components: {
        CertifactionVerification
    }
})
```

### Load locales

Example code how to load the component translations:

```js
import merge from 'lodash.merge'

import verificationDE from '@certifaction/verification-vue-component/src/locales/de.json'
import verificationEN from '@certifaction/verification-vue-component/src/locales/en.json'
import verificationFR from '@certifaction/verification-vue-component/src/locales/fr.json'
import verificationIT from '@certifaction/verification-vue-component/src/locales/it.json'

function loadLocaleMessages() {
    // Load your messages
}

const messages = merge({
    de: verificationDE,
    en: verificationEN,
    fr: verificationFR,
    it: verificationIT
}, loadLocaleMessages())

new VueI18n({
    messages
})
```

### Load stylesheet

```scss
@import "~@certifaction/verification-vue-component/src/style/components/certifaction_verification";
```

## Props

#### demo

Type: `boolean` | Required: `false` | Default: `false`

Show demo documents to see the different verification results.

#### enableClaims

Type: `boolean` | Required: `false` | Default: `true`

Enable/disable the claim based verification method.

#### providerUrl

Type: `string` | Required: `false` | Default: `https://mainnet.infura.io/v3/4876e0df8d31475799c8239ba2538c4c`

#### legacyContractAddress

Type: `string` (HEX format) | Required: `false` | Default: `0xf73e27c5008ff487803d2337fc3ac4016f6526e4`

#### legacyContractFallbackAddresses

Type: `array` (strings in HEX format) | Required: `false` | Default: `['0x5ee4ec3cbee909050e68c7ff7a8b422cfbd72244']`

#### claimContractAddress

Type: `string` (HEX format) | Required: `false` | Default: `0x5532ba4add77dd25fa11acc5a84e5f183f57525e`

#### acceptedIssuerKey

Type: `string` (HEX format) | Required: `false` | Default: `0x3b031733e215e4edf7565e11f2aba907a826aadc`

#### certifactionApiUrl

Type: `string` | Required: `false` | Default: `https://api.certifaction.io/`

#### offchainVerifier

Type: `Object<VerifierInterface>` | Required: `false` 

If you want to double check, add information, or simply make sure the user gets the correct result even though the block containing your transaction isn't finalized, you can provide a `VerifierInterface`'s implementation.

The class should only contain the method `verify(fileHash)`. The method should return the attributes you want to override.

For an example on how to do that, check [`@certifaction/verification-core/examples/CertifactionOffchainVerifierExample.js`](https://github.com/certifaction/verification/blob/master/packages/verification-core/examples/CertifactionOffchainVerifierExample.js)

## License

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/certifaction/verification/blob/master/LICENSE)

Released by [Certifaction AG](https://certifaction.io)

[npm]: https://img.shields.io/npm/v/@certifaction/verification-vue-component.svg
[npm-url]: https://www.npmjs.com/package/@certifaction/verification-vue-component
[lerna]: https://img.shields.io/badge/maintained%20with-lerna-cc00ff.svg
[lerna-url]: https://lerna.js.org/
