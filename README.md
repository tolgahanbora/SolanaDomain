# Name Service (Name Servisi)
## Name registry (Name kaydı)
Create domain with solana, like "tolgahan.sol"

Name registry stores (ad kayıt defteri), alan adıyla ilgili bilgileri depolar. İki şeyden oluşur:

**Başlık**
**Veri**
Bir alan adının verilerinin önüne her zaman başlık eklenir, JS'deki başlığın yapısı aşağıdadır:

```javascript
export class NameRegistryState {
  parentName: PublicKey;
  owner: PublicKey;
  class: PublicKey;
  data: Buffer | undefined;

  static HEADER_LEN = 96;

  static schema: Schema = new Map([
    [
      NameRegistryState,
      {
        kind: "struct",
        fields: [
          ["parentName", [32]],
          ["owner", [32]],
          ["class", [32]],
        ],
      },
    ],
  ]);

  constructor(obj: {
    parentName: Uint8Array;
    owner: Uint8Array;
    class: Uint8Array;
  }) {
    this.parentName = new PublicKey(obj.parentName);
    this.owner = new PublicKey(obj.owner);
    this.class = new PublicKey(obj.class);
  }
}
