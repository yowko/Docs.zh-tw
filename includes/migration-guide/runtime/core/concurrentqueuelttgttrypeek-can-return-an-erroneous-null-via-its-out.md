---
ms.openlocfilehash: 02a15f6b9c02002b60c568b9e1d871af49744092
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622048"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="af878-101">ConcurrentQueue&lt;T&gt;.TryPeek 可透過其 out 參數傳回錯誤的 Null</span><span class="sxs-lookup"><span data-stu-id="af878-101">ConcurrentQueue&lt;T&gt;.TryPeek can return an erroneous null via its out parameter</span></span>

#### <a name="details"></a><span data-ttu-id="af878-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="af878-102">Details</span></span>

<span data-ttu-id="af878-103">在某些多執行緒案例中，<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> 可能會傳回 true，但以 Null 值 (而不是查看到的正確值) 填入 out 參數。</span><span class="sxs-lookup"><span data-stu-id="af878-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="af878-104">建議</span><span class="sxs-lookup"><span data-stu-id="af878-104">Suggestion</span></span>

<span data-ttu-id="af878-105">此問題在 .NET Framework 4.5.1 中已修正。</span><span class="sxs-lookup"><span data-stu-id="af878-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="af878-106">升級至該 Framework 將會解決問題。</span><span class="sxs-lookup"><span data-stu-id="af878-106">Upgrading to that Framework will solve the issue.</span></span>

| <span data-ttu-id="af878-107">名稱</span><span class="sxs-lookup"><span data-stu-id="af878-107">Name</span></span>    | <span data-ttu-id="af878-108">值</span><span class="sxs-lookup"><span data-stu-id="af878-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="af878-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="af878-109">Scope</span></span>   |<span data-ttu-id="af878-110">主要</span><span class="sxs-lookup"><span data-stu-id="af878-110">Major</span></span>|
|<span data-ttu-id="af878-111">版本</span><span class="sxs-lookup"><span data-stu-id="af878-111">Version</span></span>|<span data-ttu-id="af878-112">4.5</span><span class="sxs-lookup"><span data-stu-id="af878-112">4.5</span></span>|
|<span data-ttu-id="af878-113">類型</span><span class="sxs-lookup"><span data-stu-id="af878-113">Type</span></span>|<span data-ttu-id="af878-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="af878-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="af878-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="af878-115">Affected APIs</span></span>

-<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
