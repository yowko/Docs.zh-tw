---
ms.openlocfilehash: 7682eae5a28d4ef87d6622b775e0f2f9408bcbae
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117106"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>EnvelopedCms 預設為 AES-256 加密

使用的預設對稱式加密演算法`EnvelopedCms`已從 TripleDES 變更為 AES-256

#### <a name="details"></a>詳細資料

在 .net Core Preview 7 和舊版中，當<xref:System.Security.Cryptography.Pkcs.EnvelopedCms>用來加密資料而不透過函式多載指定對稱式加密演算法時，會使用 TripleDES/3des/3DEA/DES3-EDE 演算法來加密資料。

從 .NET Core 3.0 Preview 8 開始（透過[4.6.0 的版本](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/)），預設演算法已變更為 AES-256 以進行演算法現代化，並改善預設選項的安全性。 如果訊息收件者憑證具有（非 EC） diffie-hellman 公開金鑰，加密作業可能會因基礎平臺的限制而失敗<xref:System.Security.Cryptography.CryptographicException> 。

在下列範例程式碼中，如果在 .NET Core 3.0 Preview 7 或更早版本上執行，則會使用 TripleDES 來加密資料。 如果在 .NET Core 3.0 Preview 8 或更新版本上執行，則會使用 AES-256 進行加密。

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

如果您對變更有負面影響，您可以藉由在包含型<xref:System.Security.Cryptography.Pkcs.EnvelopedCms> <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>別參數的函式中明確指定加密演算法識別碼來還原 TripleDES 加密，例如：

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>分類

密碼編譯

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->