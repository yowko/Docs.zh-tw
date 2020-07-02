---
ms.openlocfilehash: e2ae329d027d605e6331afe422e550990fab1042
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614380"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a><span data-ttu-id="3a2b7-101">預設 SignedXML 和 SignedXMS 演算法變更為 SHA256</span><span class="sxs-lookup"><span data-stu-id="3a2b7-101">Default SignedXML and SignedXMS algorithms changed to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="3a2b7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3a2b7-102">Details</span></span>

<span data-ttu-id="3a2b7-103">在 .NET Framework 4.7 和更早版本中，某些作業的 SignedXML 和 SignedCMS 預設為 SHA1。從 .NET Framework 4.7.1 開始，針對這些作業預設會啟用 SHA256。</span><span class="sxs-lookup"><span data-stu-id="3a2b7-103">In the .NET Framework 4.7 and earlier, SignedXML and SignedCMS default to SHA1 for some operations.Starting with the .NET Framework 4.7.1, SHA256 is enabled by default for these operations.</span></span> <span data-ttu-id="3a2b7-104">這項變更是必要的，因為 SHA1 不再被視為是安全的方法。</span><span class="sxs-lookup"><span data-stu-id="3a2b7-104">This change is necessary because SHA1 is no longer considered to be secure.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3a2b7-105">建議</span><span class="sxs-lookup"><span data-stu-id="3a2b7-105">Suggestion</span></span>

<span data-ttu-id="3a2b7-106">有兩個新內容參數值可以控制預設使用 SHA1 (不安全) 還是 SHA256：</span><span class="sxs-lookup"><span data-stu-id="3a2b7-106">There are two new context switch values to control whether SHA1 (insecure) or SHA256 is used by default:</span></span>

- <span data-ttu-id="3a2b7-107">Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</span><span class="sxs-lookup"><span data-stu-id="3a2b7-107">Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</span></span>
- <span data-ttu-id="3a2b7-108">Switch.System。UseInsecureHashAlgorithms 適用于以 .NET Framework 4.7.1 和更新版本為目標的應用程式，如果不想使用 SHA256，您可以將下列設定參數新增至您應用程式佈建檔的[runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)區段，將預設值還原為 SHA1：</span><span class="sxs-lookup"><span data-stu-id="3a2b7-108">Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms For applications that target the .NET Framework 4.7.1 and later versions, if the use of SHA256 is undesirable, you can restore the default to SHA1 by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true" />
```

<span data-ttu-id="3a2b7-109">若為以 .NET Framework 4.7.1 和更早版本為目標的應用程式，您可以新增下列設定參數到應用程式設定檔的 [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段，選擇加入此變更：</span><span class="sxs-lookup"><span data-stu-id="3a2b7-109">For applications that target the .NET Framework 4.7 and earlier versions, you can opt into this change by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false" />
```

| <span data-ttu-id="3a2b7-110">名稱</span><span class="sxs-lookup"><span data-stu-id="3a2b7-110">Name</span></span>    | <span data-ttu-id="3a2b7-111">值</span><span class="sxs-lookup"><span data-stu-id="3a2b7-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3a2b7-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="3a2b7-112">Scope</span></span>   | <span data-ttu-id="3a2b7-113">Minor</span><span class="sxs-lookup"><span data-stu-id="3a2b7-113">Minor</span></span>       |
| <span data-ttu-id="3a2b7-114">版本</span><span class="sxs-lookup"><span data-stu-id="3a2b7-114">Version</span></span> | <span data-ttu-id="3a2b7-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="3a2b7-115">4.7.1</span></span>       |
| <span data-ttu-id="3a2b7-116">類型</span><span class="sxs-lookup"><span data-stu-id="3a2b7-116">Type</span></span>    | <span data-ttu-id="3a2b7-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="3a2b7-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3a2b7-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3a2b7-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType>
