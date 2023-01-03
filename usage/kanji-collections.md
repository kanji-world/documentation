## Kanji Collections
To use the Kanji collections in your app, there is a specific set of hooks, depending on what collection type you want to interact with:
- DropERC721A: `useCollectionDropERC721A`
- DropERC721R: `useCollectionDropERC721R`
- DropER1155: `useCollectionDropERC1155`

---
In this example, click on the button will claim 5 tokens:
```jsx
import { useCollectionDropERC721A } from "@kanji-world/react-sdk"

//...
const [metadata, setMetadata] = useState()
const collection = useCollectionDropERC721A("0x1111111111111111111111111111111111111111")

useEffect(() => {
  collection.getContractMetadata().then(m => setMetadata(m))
},[])

return <button disabled={!collection} onClick={() => { collection.claimTokens("0x2222222222222222222222222222222222222222", 5)}} />

```