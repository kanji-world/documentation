## Installation
With npm:

`npm install @kanji-world/react-sdk`

With yarn:

`yarn add @kanji-world/react-sdk`

## Use in your project
In your `main.js` or `main.tsx` app that renders the root component, wrap it with `KanjiProvider`:
```ts
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

Right after, you will be able to call any function exported by `wagmi` and refer to their [documentation](https://wagmi.sh/examples/connect-wallet).