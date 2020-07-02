---
ms.openlocfilehash: 9131c91b34f4c24653dea37ea39af6be6e072287
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620031"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a><span data-ttu-id="88a56-101">Enumerable.Empty&lt;TResult&gt; 一律會傳回快取的執行個體</span><span class="sxs-lookup"><span data-stu-id="88a56-101">Enumerable.Empty&lt;TResult&gt; always returns cached instance</span></span>

#### <a name="details"></a><span data-ttu-id="88a56-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="88a56-102">Details</span></span>

<span data-ttu-id="88a56-103">從 .NET Framework 4.5 開始，<xref:System.Linq.Enumerable.Empty%60%601> 一律會傳回快取的內部執行個體 <xref:System.Collections.Generic.IEnumerable%601>。之前，<xref:System.Linq.Enumerable.Empty%60%601> 會在呼叫 API 時快取空的 <xref:System.Collections.Generic.IEnumerable%601>，也就是說，在快速且同時呼叫 <xref:System.Linq.Enumerable.Empty%60%601> 的某些情況下，可能會針對不同的 API 呼叫傳回不同的類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="88a56-103">Beginning in .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> always returns a cached internal instance <xref:System.Collections.Generic.IEnumerable%601>.Previously, <xref:System.Linq.Enumerable.Empty%60%601> would cache an empty <xref:System.Collections.Generic.IEnumerable%601> at the time the API was called, meaning that in some conditions in which <xref:System.Linq.Enumerable.Empty%60%601> was called rapidly and concurrently, different instances of the type could be returned for different calls to the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="88a56-104">建議</span><span class="sxs-lookup"><span data-stu-id="88a56-104">Suggestion</span></span>

<span data-ttu-id="88a56-105">由於舊版行為不具決定性，因此程式碼不太可能取決於此行為。</span><span class="sxs-lookup"><span data-stu-id="88a56-105">Because the previous behavior was non-deterministic, code is unlikely to depend on it.</span></span> <span data-ttu-id="88a56-106">不過，在罕見的情況下，如果空的可列舉值經比較有時必須不相等，則應該建立明確的空陣列 (<code>new T[0]</code>)，而不是使用 <xref:System.Linq.Enumerable.Empty%60%601>。</span><span class="sxs-lookup"><span data-stu-id="88a56-106">However, in the unlikely case that empty enumerables are being compared and expected to sometimes be unequal, explicit empty arrays should be created (<code>new T[0]</code>) instead of using <xref:System.Linq.Enumerable.Empty%60%601>.</span></span>

| <span data-ttu-id="88a56-107">名稱</span><span class="sxs-lookup"><span data-stu-id="88a56-107">Name</span></span>    | <span data-ttu-id="88a56-108">值</span><span class="sxs-lookup"><span data-stu-id="88a56-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="88a56-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="88a56-109">Scope</span></span>   |<span data-ttu-id="88a56-110">Edge</span><span class="sxs-lookup"><span data-stu-id="88a56-110">Edge</span></span>|
|<span data-ttu-id="88a56-111">版本</span><span class="sxs-lookup"><span data-stu-id="88a56-111">Version</span></span>|<span data-ttu-id="88a56-112">4.5</span><span class="sxs-lookup"><span data-stu-id="88a56-112">4.5</span></span>|
|<span data-ttu-id="88a56-113">類型</span><span class="sxs-lookup"><span data-stu-id="88a56-113">Type</span></span>|<span data-ttu-id="88a56-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="88a56-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="88a56-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="88a56-115">Affected APIs</span></span>

-<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|
