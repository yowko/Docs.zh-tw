---
ms.openlocfilehash: f9000b19997201c2d3de0643669f9029ff1ca31c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567998"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>信封Cm預設為 AES-256 加密

使用的`EnvelopedCms`預設對稱加密演算法從三重DES 更改為 AES-256。

#### <a name="change-description"></a>變更描述

在 .NET 核心預覽 7 和<xref:System.Security.Cryptography.Pkcs.EnvelopedCms>早期版本中，當用於加密資料而不通過建構函式重載指定對稱加密演算法時，資料使用 TripleDES/3DES/3DEA/DES3-EDE 演算法進行加密。

從 .NET Core 3.0 預覽 8（通過系統版本[4.6.0.Security.Crypto.Cryptoic.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet 包）開始，預設演算法已更改為 AES-256，用於演算法現代化並提高預設選項的安全性。 如果郵件收件者證書具有（非 EC）Diffie-Hellman 公開金鑰，則由於基礎平臺中的限制，加密<xref:System.Security.Cryptography.CryptographicException>操作可能會失敗。

在以下示例代碼中，如果在 .NET Core 3.0 預覽版 7 或更早版本上運行，則資料使用 TripleDES 進行加密。 如果在 .NET Core 3.0 預覽版 3.0 或更高版本上運行，則使用 AES-256 加密。

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 8

#### <a name="recommended-action"></a>建議的動作

如果受到更改的負面影響，可以通過顯式指定包含類型<xref:System.Security.Cryptography.Pkcs.EnvelopedCms><xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>參數的建構函式中的加密演算法識別碼來還原 TripleDES 加密，例如：

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>類別

Cryptography

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
