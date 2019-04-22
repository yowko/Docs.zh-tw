---
ms.openlocfilehash: 4e81087431091dfa4d5432d5ea5e2b665be2b130
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774314"
---
### <a name="listtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="58448-101">修改清單項目時，List\<T>.ForEach 可能會擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="58448-101">List\<T>.ForEach can throw exception when modifying list item</span></span>

|   |   |
|---|---|
|<span data-ttu-id="58448-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="58448-102">Details</span></span>|<span data-ttu-id="58448-103">從 .NET Framework 4.5 開始，如果呼叫集合中有任何項目遭到修改，<xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> 列舉程式將會擲回 <xref:System.InvalidOperationException?displayProperty=name> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="58448-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=name> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="58448-104">之前，這不會擲回例外狀況，但可能會造成競爭情形。</span><span class="sxs-lookup"><span data-stu-id="58448-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>|
|<span data-ttu-id="58448-105">建議</span><span class="sxs-lookup"><span data-stu-id="58448-105">Suggestion</span></span>|<span data-ttu-id="58448-106">在理想情況下，您應該修正程式碼，不要在列舉其項目時修改清單，因為這絕不是安全的作業。</span><span class="sxs-lookup"><span data-stu-id="58448-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="58448-107">不過，若要還原成舊版行為，應用程式可以將目標設為 .NET Framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="58448-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>|
|<span data-ttu-id="58448-108">範圍</span><span class="sxs-lookup"><span data-stu-id="58448-108">Scope</span></span>|<span data-ttu-id="58448-109">Edge</span><span class="sxs-lookup"><span data-stu-id="58448-109">Edge</span></span>|
|<span data-ttu-id="58448-110">版本</span><span class="sxs-lookup"><span data-stu-id="58448-110">Version</span></span>|<span data-ttu-id="58448-111">4.5</span><span class="sxs-lookup"><span data-stu-id="58448-111">4.5</span></span>|
|<span data-ttu-id="58448-112">類型</span><span class="sxs-lookup"><span data-stu-id="58448-112">Type</span></span>|<span data-ttu-id="58448-113">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="58448-113">Retargeting</span></span>|
|<span data-ttu-id="58448-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="58448-114">Affected APIs</span></span>|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|
