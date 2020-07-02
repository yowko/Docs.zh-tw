---
ms.openlocfilehash: 36a9db601f7637185bf48dfcbe2233b4489fcdcf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614329"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a><span data-ttu-id="c59a9-101">AesCryptoServiceProvider 解密程式提供可重複使用的轉換</span><span class="sxs-lookup"><span data-stu-id="c59a9-101">AesCryptoServiceProvider decryptor provides a reusable transform</span></span>

#### <a name="details"></a><span data-ttu-id="c59a9-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c59a9-102">Details</span></span>

<span data-ttu-id="c59a9-103">從以 .NET Framework 4.6.2 為目標的應用程式開始，<xref:System.Security.Cryptography.AesCryptoServiceProvider> 解密程式會提供可重複使用的轉換。</span><span class="sxs-lookup"><span data-stu-id="c59a9-103">Starting with apps that target the .NET Framework 4.6.2, the <xref:System.Security.Cryptography.AesCryptoServiceProvider> decryptor provides a reusable transform.</span></span> <span data-ttu-id="c59a9-104">呼叫 <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> 之後，轉換就會重新初始化並且可重複使用。</span><span class="sxs-lookup"><span data-stu-id="c59a9-104">After a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>, the transform is reinitialized and can be reused.</span></span> <span data-ttu-id="c59a9-105">若為以舊版 .NET Framework 為目標的應用程式，嘗試透過在呼叫 <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> 之後呼叫 <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> 來重複使用解密程式，會擲回 <xref:System.Security.Cryptography.CryptographicException> 或產生損毀的資料。</span><span class="sxs-lookup"><span data-stu-id="c59a9-105">For apps that target earlier versions of the .NET Framework, attempting to reuse the decryptor by calling <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> after a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> throws a <xref:System.Security.Cryptography.CryptographicException> or produces corrupted data.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c59a9-106">建議</span><span class="sxs-lookup"><span data-stu-id="c59a9-106">Suggestion</span></span>

<span data-ttu-id="c59a9-107">此變更的影響應該很小，因為這是預期的行為。倚賴舊行為的應用程式可以藉由將下列組態設定新增到應用程式設定檔的 `<runtime>` 區段，選擇不使用：</span><span class="sxs-lookup"><span data-stu-id="c59a9-107">The impact of this change should be minimal, since this is the expected behavior.Applications that depend on the previous behavior can opt out of it using it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
</runtime>
```

<span data-ttu-id="c59a9-108">此外，以舊版 .NET Framework 為目標，但是在從 .NET Framework 4.6.2 開始的 .NET Framework 版本下執行的應用程式，可以藉由將下列組態設定新增到應用程式設定檔的 `<runtime>` 區段，來選擇使用：</span><span class="sxs-lookup"><span data-stu-id="c59a9-108">In addition, applications that target a previous version of the .NET Framework but are running under a version of the .NET Framework starting with .NET Framework 4.6.2 can opt in to it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
</runtime>
```

| <span data-ttu-id="c59a9-109">名稱</span><span class="sxs-lookup"><span data-stu-id="c59a9-109">Name</span></span>    | <span data-ttu-id="c59a9-110">值</span><span class="sxs-lookup"><span data-stu-id="c59a9-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c59a9-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="c59a9-111">Scope</span></span>   | <span data-ttu-id="c59a9-112">Minor</span><span class="sxs-lookup"><span data-stu-id="c59a9-112">Minor</span></span>       |
| <span data-ttu-id="c59a9-113">版本</span><span class="sxs-lookup"><span data-stu-id="c59a9-113">Version</span></span> | <span data-ttu-id="c59a9-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="c59a9-114">4.6.2</span></span>       |
| <span data-ttu-id="c59a9-115">類型</span><span class="sxs-lookup"><span data-stu-id="c59a9-115">Type</span></span>    | <span data-ttu-id="c59a9-116">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="c59a9-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c59a9-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c59a9-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType>
