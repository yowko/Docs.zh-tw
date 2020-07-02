---
ms.openlocfilehash: acb5b467fc8f0692d8fa1b3b8263fd27308cc124
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617134"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a><span data-ttu-id="270b3-101">WebUtility.HtmlEncode 和 WebUtility.HtmlDecode 正確地反覆存取 BMP</span><span class="sxs-lookup"><span data-stu-id="270b3-101">WebUtility.HtmlEncode and WebUtility.HtmlDecode round-trip BMP correctly</span></span>

#### <a name="details"></a><span data-ttu-id="270b3-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="270b3-102">Details</span></span>

<span data-ttu-id="270b3-103">若是目標為 .NET Framework 4.5 的應用程式，當 Basic Multilingual Plane (BMP) 以外的字元傳遞至 <xref:System.Net.WebUtility.HtmlDecode(System.String)> 方法時，會正確地來回轉譯。</span><span class="sxs-lookup"><span data-stu-id="270b3-103">For applications that target the .NET Framework 4.5, characters that are outside the Basic Multilingual Plane (BMP) round-trip correctly when they are passed to the <xref:System.Net.WebUtility.HtmlDecode(System.String)> methods.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="270b3-104">建議</span><span class="sxs-lookup"><span data-stu-id="270b3-104">Suggestion</span></span>

<span data-ttu-id="270b3-105">這項變更應該不會影響目前的應用程式，但若要還原原始行為，請將 `targetFramework` 元素的屬性設定 `<httpRuntime>` 為 "4.5" 以外的字串。</span><span class="sxs-lookup"><span data-stu-id="270b3-105">This change should have no effect on current applications, but to restore the original behavior, set the `targetFramework` attribute of the `<httpRuntime>` element to a string other than "4.5".</span></span> <span data-ttu-id="270b3-106">您也可以設定 `unicodeEncodingConformance` 組態項目的 `unicodeDecodingConformance` 和 `<webUtility>` 屬性，以與目標 .NET Framework 版本不相關的方式控制這個行為。</span><span class="sxs-lookup"><span data-stu-id="270b3-106">You can also set the `unicodeEncodingConformance` and `unicodeDecodingConformance` attributes of the `<webUtility>` configuration element to control this behavior independently of the targeted version of the .NET Framework.</span></span>

| <span data-ttu-id="270b3-107">名稱</span><span class="sxs-lookup"><span data-stu-id="270b3-107">Name</span></span>    | <span data-ttu-id="270b3-108">值</span><span class="sxs-lookup"><span data-stu-id="270b3-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="270b3-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="270b3-109">Scope</span></span>   | <span data-ttu-id="270b3-110">Edge</span><span class="sxs-lookup"><span data-stu-id="270b3-110">Edge</span></span>        |
| <span data-ttu-id="270b3-111">版本</span><span class="sxs-lookup"><span data-stu-id="270b3-111">Version</span></span> | <span data-ttu-id="270b3-112">4.5</span><span class="sxs-lookup"><span data-stu-id="270b3-112">4.5</span></span>         |
| <span data-ttu-id="270b3-113">類型</span><span class="sxs-lookup"><span data-stu-id="270b3-113">Type</span></span>    | <span data-ttu-id="270b3-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="270b3-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="270b3-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="270b3-115">Affected APIs</span></span>

- <xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
