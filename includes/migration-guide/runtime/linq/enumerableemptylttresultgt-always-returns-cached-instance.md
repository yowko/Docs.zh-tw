---
ms.openlocfilehash: c9efbefc2bce9e21f328680795e72b62bfcd5cbd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803541"
---
### <a name="enumerableemptytresult-always-returns-cached-instance"></a><span data-ttu-id="a2a1d-101">Enumerable.Empty\<TResult> 一律會傳回快取的執行個體</span><span class="sxs-lookup"><span data-stu-id="a2a1d-101">Enumerable.Empty\<TResult> always returns cached instance</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a2a1d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a2a1d-102">Details</span></span>|<span data-ttu-id="a2a1d-103">從 .NET Framework 4.5 開始，<xref:System.Linq.Enumerable.Empty%60%601> 一律會傳回快取的內部執行個體 <xref:System.Collections.Generic.IEnumerable%601>。之前，<xref:System.Linq.Enumerable.Empty%60%601> 會在呼叫 API 時快取空的 <xref:System.Collections.Generic.IEnumerable%601>，也就是說，在快速且同時呼叫 <xref:System.Linq.Enumerable.Empty%60%601> 的某些情況下，可能會針對不同的 API 呼叫傳回不同的類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="a2a1d-103">Beginning in .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> always returns a cached internal instance <xref:System.Collections.Generic.IEnumerable%601>.Previously, <xref:System.Linq.Enumerable.Empty%60%601> would cache an empty <xref:System.Collections.Generic.IEnumerable%601> at the time the API was called, meaning that in some conditions in which <xref:System.Linq.Enumerable.Empty%60%601> was called rapidly and concurrently, different instances of the type could be returned for different calls to the API.</span></span>|
|<span data-ttu-id="a2a1d-104">建議</span><span class="sxs-lookup"><span data-stu-id="a2a1d-104">Suggestion</span></span>|<span data-ttu-id="a2a1d-105">由於舊版行為不具決定性，因此程式碼不太可能取決於此行為。</span><span class="sxs-lookup"><span data-stu-id="a2a1d-105">Because the previous behavior was non-deterministic, code is unlikely to depend on it.</span></span> <span data-ttu-id="a2a1d-106">不過，在罕見的情況下，如果空的可列舉值經比較有時必須不相等，則應該建立明確的空陣列 (<code>new T[0]</code>)，而不是使用 <xref:System.Linq.Enumerable.Empty%60%601>。</span><span class="sxs-lookup"><span data-stu-id="a2a1d-106">However, in the unlikely case that empty enumerables are being compared and expected to sometimes be unequal, explicit empty arrays should be created (<code>new T[0]</code>) instead of using <xref:System.Linq.Enumerable.Empty%60%601>.</span></span>|
|<span data-ttu-id="a2a1d-107">範圍</span><span class="sxs-lookup"><span data-stu-id="a2a1d-107">Scope</span></span>|<span data-ttu-id="a2a1d-108">Edge</span><span class="sxs-lookup"><span data-stu-id="a2a1d-108">Edge</span></span>|
|<span data-ttu-id="a2a1d-109">版本</span><span class="sxs-lookup"><span data-stu-id="a2a1d-109">Version</span></span>|<span data-ttu-id="a2a1d-110">4.5</span><span class="sxs-lookup"><span data-stu-id="a2a1d-110">4.5</span></span>|
|<span data-ttu-id="a2a1d-111">類型</span><span class="sxs-lookup"><span data-stu-id="a2a1d-111">Type</span></span>|<span data-ttu-id="a2a1d-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="a2a1d-112">Runtime</span></span>|
|<span data-ttu-id="a2a1d-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a2a1d-113">Affected APIs</span></span>|<ul><li><xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|
