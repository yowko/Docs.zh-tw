---
ms.openlocfilehash: e0cdcce9b8c7d591925b08635e3354dadaf22b7b
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556019"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="6ed1d-101">EnvelopedCms 預設為 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="6ed1d-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="6ed1d-102">使用的預設對稱式加密演算法 `EnvelopedCms` 已從 TripleDES 變更為 AES-256。</span><span class="sxs-lookup"><span data-stu-id="6ed1d-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6ed1d-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="6ed1d-103">Change description</span></span>

<span data-ttu-id="6ed1d-104">在舊版中，當 <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> 用來加密資料，而不透過函式多載指定對稱式加密演算法時，資料會使用 TripleDES/3des/3DEA/DES3-EDE 演算法來加密。</span><span class="sxs-lookup"><span data-stu-id="6ed1d-104">In previous versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data is encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="6ed1d-105">從 .NET Core 3.0 開始 (透過4.6.0 的[System.](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/)) 的版本，預設演算法已變更為 AES-256 以進行演算法現代化，並改善預設選項的安全性。</span><span class="sxs-lookup"><span data-stu-id="6ed1d-105">Starting with .NET Core 3.0 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="6ed1d-106">如果訊息收件者憑證具有 (非 EC) Diffie-hellman 公開金鑰，則加密作業可能會因 <xref:System.Security.Cryptography.CryptographicException> 基礎平臺的限制而失敗。</span><span class="sxs-lookup"><span data-stu-id="6ed1d-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="6ed1d-107">在下列範例程式碼中，如果在 .NET Core 2.2 或更早版本上執行，則會使用 TripleDES 來加密資料。</span><span class="sxs-lookup"><span data-stu-id="6ed1d-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 2.2 or earlier.</span></span> <span data-ttu-id="6ed1d-108">如果在 .NET Core 3.0 或更新版本上執行，則會使用 AES-256 進行加密。</span><span class="sxs-lookup"><span data-stu-id="6ed1d-108">If running on .NET Core 3.0 or later, it's encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="6ed1d-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6ed1d-109">Version introduced</span></span>

<span data-ttu-id="6ed1d-110">3.0</span><span class="sxs-lookup"><span data-stu-id="6ed1d-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6ed1d-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="6ed1d-111">Recommended action</span></span>

<span data-ttu-id="6ed1d-112">如果您對變更有負面影響，您可以藉由在包含型別參數的函式中明確指定加密演算法識別碼來還原 TripleDES 加密 <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier> ，例如：</span><span class="sxs-lookup"><span data-stu-id="6ed1d-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="6ed1d-113">類別</span><span class="sxs-lookup"><span data-stu-id="6ed1d-113">Category</span></span>

<span data-ttu-id="6ed1d-114">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="6ed1d-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6ed1d-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6ed1d-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
