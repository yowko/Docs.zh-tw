---
ms.openlocfilehash: ca662b57fae9b1d0d41290f3052f71bca66e9bf3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774377"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a><span data-ttu-id="32ba6-101">WebUtility.HtmlEncode 和 WebUtility.HtmlDecode 正確地反覆存取 BMP</span><span class="sxs-lookup"><span data-stu-id="32ba6-101">WebUtility.HtmlEncode and WebUtility.HtmlDecode round-trip BMP correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="32ba6-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="32ba6-102">Details</span></span>|<span data-ttu-id="32ba6-103">若是目標為 .NET Framework 4.5 的應用程式，當 Basic Multilingual Plane (BMP) 以外的字元傳遞至 <xref:System.Net.WebUtility.HtmlDecode(System.String)> 方法時，會正確地來回轉譯。</span><span class="sxs-lookup"><span data-stu-id="32ba6-103">For applications that target the .NET Framework 4.5, characters that are outside the Basic Multilingual Plane (BMP) round-trip correctly when they are passed to the <xref:System.Net.WebUtility.HtmlDecode(System.String)> methods.</span></span>|
|<span data-ttu-id="32ba6-104">建議</span><span class="sxs-lookup"><span data-stu-id="32ba6-104">Suggestion</span></span>|<span data-ttu-id="32ba6-105">這項變更應該不會影響目前的應用程式，但若要還原原始行為，請將 <code>&lt;httpRuntime&gt;</code> 項目的 <code>targetFramework</code> 屬性設為非 &quot;4.5&quot; 的字串。</span><span class="sxs-lookup"><span data-stu-id="32ba6-105">This change should have no effect on current applications, but to restore the original behavior, set the <code>targetFramework</code> attribute of the <code>&lt;httpRuntime&gt;</code> element to a string other than &quot;4.5&quot;.</span></span> <span data-ttu-id="32ba6-106">您也可以設定 <code>unicodeEncodingConformance</code> 組態項目的 <code>unicodeDecodingConformance</code> 和 <code>&lt;webUtility&gt;</code> 屬性，以與目標 .NET Framework 版本不相關的方式控制這個行為。</span><span class="sxs-lookup"><span data-stu-id="32ba6-106">You can also set the <code>unicodeEncodingConformance</code> and <code>unicodeDecodingConformance</code> attributes of the <code>&lt;webUtility&gt;</code> configuration element to control this behavior independently of the targeted version of the .NET Framework.</span></span>|
|<span data-ttu-id="32ba6-107">範圍</span><span class="sxs-lookup"><span data-stu-id="32ba6-107">Scope</span></span>|<span data-ttu-id="32ba6-108">Edge</span><span class="sxs-lookup"><span data-stu-id="32ba6-108">Edge</span></span>|
|<span data-ttu-id="32ba6-109">版本</span><span class="sxs-lookup"><span data-stu-id="32ba6-109">Version</span></span>|<span data-ttu-id="32ba6-110">4.5</span><span class="sxs-lookup"><span data-stu-id="32ba6-110">4.5</span></span>|
|<span data-ttu-id="32ba6-111">類型</span><span class="sxs-lookup"><span data-stu-id="32ba6-111">Type</span></span>|<span data-ttu-id="32ba6-112">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="32ba6-112">Retargeting</span></span>|
|<span data-ttu-id="32ba6-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="32ba6-113">Affected APIs</span></span>|<ul><li><xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li></ul>|
