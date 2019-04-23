---
ms.openlocfilehash: a93fbbd787aa50f080337a6170cf8f56d0d24e31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803491"
---
### <a name="concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="19627-101">ConcurrentQueue\<T>.TryPeek 可透過其 out 參數傳回錯誤的 Null</span><span class="sxs-lookup"><span data-stu-id="19627-101">ConcurrentQueue\<T>.TryPeek can return an erroneous null via its out parameter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="19627-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="19627-102">Details</span></span>|<span data-ttu-id="19627-103">在某些多執行緒案例中，<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> 可能會傳回 true，但以 Null 值 (而不是查看到的正確值) 填入 out 參數。</span><span class="sxs-lookup"><span data-stu-id="19627-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>|
|<span data-ttu-id="19627-104">建議</span><span class="sxs-lookup"><span data-stu-id="19627-104">Suggestion</span></span>|<span data-ttu-id="19627-105">此問題在 .NET Framework 4.5.1 中已修正。</span><span class="sxs-lookup"><span data-stu-id="19627-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="19627-106">升級至該 Framework 將會解決問題。</span><span class="sxs-lookup"><span data-stu-id="19627-106">Upgrading to that Framework will solve the issue.</span></span>|
|<span data-ttu-id="19627-107">範圍</span><span class="sxs-lookup"><span data-stu-id="19627-107">Scope</span></span>|<span data-ttu-id="19627-108">主要</span><span class="sxs-lookup"><span data-stu-id="19627-108">Major</span></span>|
|<span data-ttu-id="19627-109">版本</span><span class="sxs-lookup"><span data-stu-id="19627-109">Version</span></span>|<span data-ttu-id="19627-110">4.5</span><span class="sxs-lookup"><span data-stu-id="19627-110">4.5</span></span>|
|<span data-ttu-id="19627-111">類型</span><span class="sxs-lookup"><span data-stu-id="19627-111">Type</span></span>|<span data-ttu-id="19627-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="19627-112">Runtime</span></span>|
|<span data-ttu-id="19627-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="19627-113">Affected APIs</span></span>|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
