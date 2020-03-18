---
ms.openlocfilehash: f9000b19997201c2d3de0643669f9029ff1ca31c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567998"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="a3f0c-101">信封Cm預設為 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="a3f0c-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="a3f0c-102">使用的`EnvelopedCms`預設對稱加密演算法從三重DES 更改為 AES-256。</span><span class="sxs-lookup"><span data-stu-id="a3f0c-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a3f0c-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="a3f0c-103">Change description</span></span>

<span data-ttu-id="a3f0c-104">在 .NET 核心預覽 7 和<xref:System.Security.Cryptography.Pkcs.EnvelopedCms>早期版本中，當用於加密資料而不通過建構函式重載指定對稱加密演算法時，資料使用 TripleDES/3DES/3DEA/DES3-EDE 演算法進行加密。</span><span class="sxs-lookup"><span data-stu-id="a3f0c-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="a3f0c-105">從 .NET Core 3.0 預覽 8（通過系統版本[4.6.0.Security.Crypto.Cryptoic.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet 包）開始，預設演算法已更改為 AES-256，用於演算法現代化並提高預設選項的安全性。</span><span class="sxs-lookup"><span data-stu-id="a3f0c-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="a3f0c-106">如果郵件收件者證書具有（非 EC）Diffie-Hellman 公開金鑰，則由於基礎平臺中的限制，加密<xref:System.Security.Cryptography.CryptographicException>操作可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="a3f0c-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="a3f0c-107">在以下示例代碼中，如果在 .NET Core 3.0 預覽版 7 或更早版本上運行，則資料使用 TripleDES 進行加密。</span><span class="sxs-lookup"><span data-stu-id="a3f0c-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="a3f0c-108">如果在 .NET Core 3.0 預覽版 3.0 或更高版本上運行，則使用 AES-256 加密。</span><span class="sxs-lookup"><span data-stu-id="a3f0c-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="a3f0c-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="a3f0c-109">Version introduced</span></span>

<span data-ttu-id="a3f0c-110">3.0 預覽 8</span><span class="sxs-lookup"><span data-stu-id="a3f0c-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a3f0c-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="a3f0c-111">Recommended action</span></span>

<span data-ttu-id="a3f0c-112">如果受到更改的負面影響，可以通過顯式指定包含類型<xref:System.Security.Cryptography.Pkcs.EnvelopedCms><xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>參數的建構函式中的加密演算法識別碼來還原 TripleDES 加密，例如：</span><span class="sxs-lookup"><span data-stu-id="a3f0c-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="a3f0c-113">類別</span><span class="sxs-lookup"><span data-stu-id="a3f0c-113">Category</span></span>

<span data-ttu-id="a3f0c-114">Cryptography</span><span class="sxs-lookup"><span data-stu-id="a3f0c-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a3f0c-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a3f0c-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
