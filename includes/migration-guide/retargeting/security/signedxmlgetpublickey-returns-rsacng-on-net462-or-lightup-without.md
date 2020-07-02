---
ms.openlocfilehash: 23e278d38d6904d8afe927e6b54c388d443e41f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616035"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a><span data-ttu-id="a905f-101">SignedXml.GetPublicKey RSACng 會在 net462 (或 lightup) 上傳回 RSACng，而無重定目標變更</span><span class="sxs-lookup"><span data-stu-id="a905f-101">SignedXml.GetPublicKey returns RSACng on net462 (or lightup) without retargeting change</span></span>

#### <a name="details"></a><span data-ttu-id="a905f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a905f-102">Details</span></span>

<span data-ttu-id="a905f-103">從 .NET Framework 4.6.2 開始，<xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> 方法所傳回的物件具象類型 (毫不奇怪地) 從 CryptoServiceProvider 實作變更為 Cng 實作。</span><span class="sxs-lookup"><span data-stu-id="a905f-103">Starting with the .NET Framework 4.6.2, the concrete type of the object returned by the <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> method changed (without a quirk) from a CryptoServiceProvider implementation to a Cng implementation.</span></span> <span data-ttu-id="a905f-104">這是因為實作從使用 `certificate.PublicKey.Key` 變更為使用內部 `certificate.GetAnyPublicKey`，它會轉送給 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a905f-104">This is because the implementation changed from using `certificate.PublicKey.Key` to using the internal `certificate.GetAnyPublicKey` which forwards to <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a905f-105">建議</span><span class="sxs-lookup"><span data-stu-id="a905f-105">Suggestion</span></span>

<span data-ttu-id="a905f-106">從在 .NET Framework 4.7.1 上執行的應用程式開始，您可以使用 .NET Framework 4.6.1 和更早版本中預設使用的 CryptoServiceProvider 實作，方法是將下列設定參數新增至您應用程式設定檔的 [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段：</span><span class="sxs-lookup"><span data-stu-id="a905f-106">Starting with apps running on the .NET Framework 4.7.1, you can use the CryptoServiceProvider implementation used by default in the .NET Framework 4.6.1 and earlier versions by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true" />
```

| <span data-ttu-id="a905f-107">名稱</span><span class="sxs-lookup"><span data-stu-id="a905f-107">Name</span></span>    | <span data-ttu-id="a905f-108">值</span><span class="sxs-lookup"><span data-stu-id="a905f-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a905f-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="a905f-109">Scope</span></span>   | <span data-ttu-id="a905f-110">Edge</span><span class="sxs-lookup"><span data-stu-id="a905f-110">Edge</span></span>        |
| <span data-ttu-id="a905f-111">版本</span><span class="sxs-lookup"><span data-stu-id="a905f-111">Version</span></span> | <span data-ttu-id="a905f-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="a905f-112">4.6.2</span></span>       |
| <span data-ttu-id="a905f-113">類型</span><span class="sxs-lookup"><span data-stu-id="a905f-113">Type</span></span>    | <span data-ttu-id="a905f-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="a905f-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="a905f-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a905f-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType>
