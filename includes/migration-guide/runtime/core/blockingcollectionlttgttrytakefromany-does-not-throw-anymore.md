---
ms.openlocfilehash: 277a91fbfbf0c6aaaa0dc044ef0c079ad8607699
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497225"
---
### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a><span data-ttu-id="acb18-101">lBlockingCollection&lt;T&gt;.TryTakeFromAny 不會再擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="acb18-101">BlockingCollection&lt;T&gt;.TryTakeFromAny does not throw anymore</span></span>

#### <a name="details"></a><span data-ttu-id="acb18-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="acb18-102">Details</span></span>

<span data-ttu-id="acb18-103">如果其中一個輸入集合標記為已完成，則 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> 不會再傳回 -1，而且 <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> 不會再擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="acb18-103">If one of the input collections is marked completed, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer returns -1 and <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer throws an exception.</span></span> <span data-ttu-id="acb18-104">這項變更能夠讓您在其中一個集合為空集合或已完成，而另一個集合仍有可擷取的項目時處理集合。</span><span class="sxs-lookup"><span data-stu-id="acb18-104">This change makes it possible to work with collections when one of the collections is either empty or completed, but the other collection still has items that can be retrieved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="acb18-105">建議</span><span class="sxs-lookup"><span data-stu-id="acb18-105">Suggestion</span></span>

<span data-ttu-id="acb18-106">如果在防止集合完成時，使用了傳回 -1 的 TryTakeFromAny 或擲回的 TakeFromAny 來控制流程，現在應該將這類程式碼變更為使用 <code>.Any(b =&gt; b.IsCompleted)</code> 來偵測該情況。</span><span class="sxs-lookup"><span data-stu-id="acb18-106">If TryTakeFromAny returning -1 or TakeFromAny throwing were used for control-flow purposes in cases of a blocking collection being completed, such code should now be changed to use <code>.Any(b =&gt; b.IsCompleted)</code> to detect that condition.</span></span>

| <span data-ttu-id="acb18-107">名稱</span><span class="sxs-lookup"><span data-stu-id="acb18-107">Name</span></span>    | <span data-ttu-id="acb18-108">值</span><span class="sxs-lookup"><span data-stu-id="acb18-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="acb18-109">範圍</span><span class="sxs-lookup"><span data-stu-id="acb18-109">Scope</span></span>   |<span data-ttu-id="acb18-110">Minor</span><span class="sxs-lookup"><span data-stu-id="acb18-110">Minor</span></span>|
|<span data-ttu-id="acb18-111">版本</span><span class="sxs-lookup"><span data-stu-id="acb18-111">Version</span></span>|<span data-ttu-id="acb18-112">4.5</span><span class="sxs-lookup"><span data-stu-id="acb18-112">4.5</span></span>|
|<span data-ttu-id="acb18-113">類型</span><span class="sxs-lookup"><span data-stu-id="acb18-113">Type</span></span>|<span data-ttu-id="acb18-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="acb18-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="acb18-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="acb18-115">Affected APIs</span></span>

- <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Concurrent.BlockingCollection`1.TakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.Threading.CancellationToken)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.Int32)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.TimeSpan)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.TimeSpan)``

-->
