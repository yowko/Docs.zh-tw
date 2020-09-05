---
ms.openlocfilehash: 004e2d1883b631e88ab5e164b1120c3b081b7041
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497527"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="764ca-101">ConcurrentQueue&lt;T&gt;.TryPeek 可透過其 out 參數傳回錯誤的 Null</span><span class="sxs-lookup"><span data-stu-id="764ca-101">ConcurrentQueue&lt;T&gt;.TryPeek can return an erroneous null via its out parameter</span></span>

#### <a name="details"></a><span data-ttu-id="764ca-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="764ca-102">Details</span></span>

<span data-ttu-id="764ca-103">在某些多執行緒案例中，<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> 可能會傳回 true，但以 Null 值 (而不是查看到的正確值) 填入 out 參數。</span><span class="sxs-lookup"><span data-stu-id="764ca-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="764ca-104">建議</span><span class="sxs-lookup"><span data-stu-id="764ca-104">Suggestion</span></span>

<span data-ttu-id="764ca-105">此問題在 .NET Framework 4.5.1 中已修正。</span><span class="sxs-lookup"><span data-stu-id="764ca-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="764ca-106">升級至該 Framework 將會解決問題。</span><span class="sxs-lookup"><span data-stu-id="764ca-106">Upgrading to that Framework will solve the issue.</span></span>

| <span data-ttu-id="764ca-107">名稱</span><span class="sxs-lookup"><span data-stu-id="764ca-107">Name</span></span>    | <span data-ttu-id="764ca-108">值</span><span class="sxs-lookup"><span data-stu-id="764ca-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="764ca-109">範圍</span><span class="sxs-lookup"><span data-stu-id="764ca-109">Scope</span></span>   |<span data-ttu-id="764ca-110">主要</span><span class="sxs-lookup"><span data-stu-id="764ca-110">Major</span></span>|
|<span data-ttu-id="764ca-111">版本</span><span class="sxs-lookup"><span data-stu-id="764ca-111">Version</span></span>|<span data-ttu-id="764ca-112">4.5</span><span class="sxs-lookup"><span data-stu-id="764ca-112">4.5</span></span>|
|<span data-ttu-id="764ca-113">類型</span><span class="sxs-lookup"><span data-stu-id="764ca-113">Type</span></span>|<span data-ttu-id="764ca-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="764ca-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="764ca-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="764ca-115">Affected APIs</span></span>

- <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Concurrent.ConcurrentQueue`1.TryPeek(`0@)``

-->
