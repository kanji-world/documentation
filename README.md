---
description: Getting started with the SDK
cover: .gitbook/assets/kanji_hero_banner.png
coverY: -219.72192513368984
---

# React SDK

## Foreword

The kanji SDK (software development kit) aims to provide simple tools to manipulate smart contracts and the various resources created on the [studio platform](https://studio.kanji.io).

It is built on top of [`wagmi`](https://github.com/wagmi-dev/wagmi) and [`@rainbow-me/rainbowkit`](https://github.com/rainbow-me/rainbowkit) to apply to industry-leading solutions.

### Installation

{% tabs %}
{% tab title="npm" %}
```bash
npm install @kanji-world/react-sdk
```
{% endtab %}

{% tab title="yarn" %}
```bash
yarn add @kanji-world/react-sdk
```
{% endtab %}
{% endtabs %}

### Use in your project

In your `main.js` or `main.tsx` app that renders the root component, wrap it with `KanjiProvider`:

{% code lineNumbers="true" %}
```typescript
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'
import { KanjiProvider } from '@kanji-world/react-sdk'

ReactDOM.createRoot(document.getElementById('root') as HTMLElement).render(
  <KanjiProvider>
    <App />
  </KanjiProvider>,
)
```
{% endcode %}

Right after, you will be able to call any function exported by `wagmi` and refer to their [documentation](https://wagmi.sh/examples/connect-wallet).

### Kanji Collections

To use the Kanji collections in your app, there is a specific set of hooks, depending on what collection type you want to interact with:

* DropERC721A: `useCollectionDropERC721A`
* DropERC721R: `useCollectionDropERC721R`
* DropER1155: `useCollectionDropERC1155`

In this example, clicking on the button will claim 5 tokens:

```typescript
import { useCollectionDropERC721A } from "@kanji-world/react-sdk"

//...
const [metadata, setMetadata] = useState()
const collection = useCollectionDropERC721A("0x1111111111111111111111111111111111111111")

useEffect(() => {
  collection.getContractMetadata().then(m => setMetadata(m))
},[])

return <button disabled={!collection} onClick={() => { collection.claimTokens("0x2222222222222222222222222222222222222222", 5)}} />
```
