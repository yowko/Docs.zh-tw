---
ms.openlocfilehash: 80d4bbbfe52ab9685d7ca54f21b80d4b1773da22
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859634"
---
### <a name="webclientcancelasync-doesnt-always-cancel-immediately"></a><span data-ttu-id="10ee5-101">WebClient 地說 cancelasync 不一定會立即取消</span><span class="sxs-lookup"><span data-stu-id="10ee5-101">WebClient.CancelAsync doesn't always cancel immediately</span></span>

<span data-ttu-id="10ee5-102">從 .NET Core 2.0 開始，如果<xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType>已開始提取回應，呼叫就不會立即取消要求。</span><span class="sxs-lookup"><span data-stu-id="10ee5-102">Starting in .NET Core 2.0, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> doesn't cancel the request immediately if the response has started to fetch.</span></span>

#### <a name="change-description"></a><span data-ttu-id="10ee5-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="10ee5-103">Change description</span></span>

<span data-ttu-id="10ee5-104">先前呼叫<xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType>會立即取消要求。</span><span class="sxs-lookup"><span data-stu-id="10ee5-104">Previously, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> canceled the request immediately.</span></span> <span data-ttu-id="10ee5-105">從 .NET Core 2.0 開始，只有<xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType>在回應尚未開始提取時，呼叫才會立即取消要求。</span><span class="sxs-lookup"><span data-stu-id="10ee5-105">Starting in .NET Core 2.0, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> cancels the request immediately only if the response hasn't started fetching.</span></span> <span data-ttu-id="10ee5-106">如果已開始提取回應，則只會在讀取完整的回應之後，才會取消要求。</span><span class="sxs-lookup"><span data-stu-id="10ee5-106">If the response has started to fetch, the request is cancelled only after a complete response is read.</span></span>

<span data-ttu-id="10ee5-107">這項變更已實行， <xref:System.Net.WebClient>因為 API 已淘汰而改用<xref:System.Net.Http.HttpClient>。</span><span class="sxs-lookup"><span data-stu-id="10ee5-107">This change was implemented because the <xref:System.Net.WebClient> API is deprecated in favor of <xref:System.Net.Http.HttpClient>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="10ee5-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="10ee5-108">Version introduced</span></span>

<span data-ttu-id="10ee5-109">2.0</span><span class="sxs-lookup"><span data-stu-id="10ee5-109">2.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="10ee5-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="10ee5-110">Recommended action</span></span>

<span data-ttu-id="10ee5-111"><xref:System.Net.WebClient?displayProperty=fullName>請使用<xref:System.Net.Http.HttpClient?displayProperty=fullName>類別，而不是已被取代的。</span><span class="sxs-lookup"><span data-stu-id="10ee5-111">Use the <xref:System.Net.Http.HttpClient?displayProperty=fullName> class instead of <xref:System.Net.WebClient?displayProperty=fullName>, which is deprecated.</span></span>

#### <a name="category"></a><span data-ttu-id="10ee5-112">類別</span><span class="sxs-lookup"><span data-stu-id="10ee5-112">Category</span></span>

<span data-ttu-id="10ee5-113">網路功能</span><span class="sxs-lookup"><span data-stu-id="10ee5-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="10ee5-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="10ee5-114">Affected APIs</span></span>

- <xref:System.Net.WebClient.CancelAsync?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.WebClient.CancelAsync`

-->
