---
ms.openlocfilehash: b90991affe158286f535f3cc17232efd0b730fec
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275347"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="f0f76-101">信封Cm預設為 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="f0f76-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="f0f76-102">使用的`EnvelopedCms`預設對稱加密演演演算法從三重DES 更改為 AES-256。</span><span class="sxs-lookup"><span data-stu-id="f0f76-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f0f76-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="f0f76-103">Change description</span></span>

<span data-ttu-id="f0f76-104">在 .NET 核心預覽<xref:System.Security.Cryptography.Pkcs.EnvelopedCms>7 和早期版本中,當用於加密數據而不通過構造函數重載指定對稱加密演演演算法時,數據使用 TripleDES/3DES/3DEA/DES3-EDE 演算法進行加密。</span><span class="sxs-lookup"><span data-stu-id="f0f76-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="f0f76-105">從 .NET Core 3.0 預覽 8(通過系統版本[4.6.0.Security.Crypto.Cryptoic.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet 包)開始,默認演演演算法已更改為 AES-256,用於演演演演算法現代化並提高預設選項的安全性。</span><span class="sxs-lookup"><span data-stu-id="f0f76-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="f0f76-106">如果郵件收件者證書具有(非 EC)Diffie-Hellman 公鑰,則由於基礎平臺中的限制<xref:System.Security.Cryptography.CryptographicException>,加密 操作可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="f0f76-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="f0f76-107">在以下範例代碼中,如果在 .NET Core 3.0 預覽版 7 或更早版本上運行,則數據使用 TripleDES 進行加密。</span><span class="sxs-lookup"><span data-stu-id="f0f76-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="f0f76-108">如果在 .NET Core 3.0 預覽版 3.0 或更高版本上運行,則使用 AES-256 加密。</span><span class="sxs-lookup"><span data-stu-id="f0f76-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="f0f76-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f0f76-109">Version introduced</span></span>

<span data-ttu-id="f0f76-110">3.0 預覽 8</span><span class="sxs-lookup"><span data-stu-id="f0f76-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f0f76-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f0f76-111">Recommended action</span></span>

<span data-ttu-id="f0f76-112">如果受到更改的負面影響,可以通過顯式指定包含<xref:System.Security.Cryptography.Pkcs.EnvelopedCms><xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>類型 參數的構造函數中的加密演算法標識符來還原 TripleDES 加密,例如:</span><span class="sxs-lookup"><span data-stu-id="f0f76-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="f0f76-113">類別</span><span class="sxs-lookup"><span data-stu-id="f0f76-113">Category</span></span>

<span data-ttu-id="f0f76-114">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="f0f76-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f0f76-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f0f76-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
