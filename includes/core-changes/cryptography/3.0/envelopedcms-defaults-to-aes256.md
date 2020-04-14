---
ms.openlocfilehash: b90991affe158286f535f3cc17232efd0b730fec
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275347"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>信封Cm預設為 AES-256 加密

使用的`EnvelopedCms`預設對稱加密演演演算法從三重DES 更改為 AES-256。

#### <a name="change-description"></a>變更描述

在 .NET 核心預覽<xref:System.Security.Cryptography.Pkcs.EnvelopedCms>7 和早期版本中,當用於加密數據而不通過構造函數重載指定對稱加密演演演算法時,數據使用 TripleDES/3DES/3DEA/DES3-EDE 演算法進行加密。

從 .NET Core 3.0 預覽 8(通過系統版本[4.6.0.Security.Crypto.Cryptoic.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet 包)開始,默認演演演算法已更改為 AES-256,用於演演演演算法現代化並提高預設選項的安全性。 如果郵件收件者證書具有(非 EC)Diffie-Hellman 公鑰,則由於基礎平臺中的限制<xref:System.Security.Cryptography.CryptographicException>,加密 操作可能會失敗。

在以下範例代碼中,如果在 .NET Core 3.0 預覽版 7 或更早版本上運行,則數據使用 TripleDES 進行加密。 如果在 .NET Core 3.0 預覽版 3.0 或更高版本上運行,則使用 AES-256 加密。

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 8

#### <a name="recommended-action"></a>建議的動作

如果受到更改的負面影響,可以通過顯式指定包含<xref:System.Security.Cryptography.Pkcs.EnvelopedCms><xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>類型 參數的構造函數中的加密演算法標識符來還原 TripleDES 加密,例如:

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>類別

密碼編譯

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
