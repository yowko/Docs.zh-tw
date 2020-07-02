---
ms.openlocfilehash: 3300a74b81fc9eeba670ee0ceb2c2615fd3925bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617142"
---
### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="9377c-101">修改清單項目時，List&lt;T&gt;.ForEach 可能會擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="9377c-101">List&lt;T&gt;.ForEach can throw exception when modifying list item</span></span>

#### <a name="details"></a><span data-ttu-id="9377c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9377c-102">Details</span></span>

<span data-ttu-id="9377c-103">從 .NET Framework 4.5 開始，如果呼叫集合中有任何項目遭到修改，<xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> 列舉程式將會擲回 <xref:System.InvalidOperationException?displayProperty=fullName> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9377c-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=fullName> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="9377c-104">之前，這不會擲回例外狀況，但可能會造成競爭情形。</span><span class="sxs-lookup"><span data-stu-id="9377c-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9377c-105">建議</span><span class="sxs-lookup"><span data-stu-id="9377c-105">Suggestion</span></span>

<span data-ttu-id="9377c-106">在理想情況下，您應該修正程式碼，不要在列舉其項目時修改清單，因為這絕不是安全的作業。</span><span class="sxs-lookup"><span data-stu-id="9377c-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="9377c-107">不過，若要還原成舊版行為，應用程式可以將目標設為 .NET Framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="9377c-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>

| <span data-ttu-id="9377c-108">名稱</span><span class="sxs-lookup"><span data-stu-id="9377c-108">Name</span></span>    | <span data-ttu-id="9377c-109">值</span><span class="sxs-lookup"><span data-stu-id="9377c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9377c-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="9377c-110">Scope</span></span>   | <span data-ttu-id="9377c-111">Edge</span><span class="sxs-lookup"><span data-stu-id="9377c-111">Edge</span></span>        |
| <span data-ttu-id="9377c-112">版本</span><span class="sxs-lookup"><span data-stu-id="9377c-112">Version</span></span> | <span data-ttu-id="9377c-113">4.5</span><span class="sxs-lookup"><span data-stu-id="9377c-113">4.5</span></span>         |
| <span data-ttu-id="9377c-114">類型</span><span class="sxs-lookup"><span data-stu-id="9377c-114">Type</span></span>    | <span data-ttu-id="9377c-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="9377c-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="9377c-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9377c-116">Affected APIs</span></span>

- <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType>
