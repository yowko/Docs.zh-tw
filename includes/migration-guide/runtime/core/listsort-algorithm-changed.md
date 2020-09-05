---
ms.openlocfilehash: 09bd2c6312493f8b6369d05d8f1c4e88e4c05ece
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497162"
---
### <a name="listsort-algorithm-changed"></a><span data-ttu-id="a565f-101">List.Sort 演算法已變更</span><span class="sxs-lookup"><span data-stu-id="a565f-101">List.Sort algorithm changed</span></span>

#### <a name="details"></a><span data-ttu-id="a565f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a565f-102">Details</span></span>

<span data-ttu-id="a565f-103">從 .NET Framework 4.5 開始，<xref:System.Collections.Generic.List%601?displayProperty=fullName> 的排序演算法已變更 (變更為內省式排序，而不是快速排序)。</span><span class="sxs-lookup"><span data-stu-id="a565f-103">Beginning in .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort algorithm has changed (to be an introspective sort instead of a quick sort).</span></span> <span data-ttu-id="a565f-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName> 的排序從未穩定，但這項變更可能會導致不同的案例以不穩定的方式排序。</span><span class="sxs-lookup"><span data-stu-id="a565f-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort has never been stable, but this change may cause different scenarios to sort in unstable ways.</span></span> <span data-ttu-id="a565f-105">這只是表示對等項目可能會在 API 的後續呼叫中以不同的順序排序。</span><span class="sxs-lookup"><span data-stu-id="a565f-105">That simply means that equivalent items may sort in different orders in subsequent calls of the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a565f-106">建議</span><span class="sxs-lookup"><span data-stu-id="a565f-106">Suggestion</span></span>

<span data-ttu-id="a565f-107">因為舊的排序演算法也不穩定 (儘管方式略有不同)，應該沒有任何程式碼相依於一律以特定順序排序的對等項目。</span><span class="sxs-lookup"><span data-stu-id="a565f-107">Because the old sort algorithm was also unstable (though in slightly different ways), there should be no code that depends on equivalent items always sorting in a particular order.</span></span> <span data-ttu-id="a565f-108">如果有程式碼的執行個體相依於該項目，且湊巧使用舊行為，該程式碼應該更新為使用將明確地以所需順序排序項目的比較子。</span><span class="sxs-lookup"><span data-stu-id="a565f-108">If there are instances of code depending upon that and being lucky with the old behavior, that code should be updated to use a comparer that will deterministically sort the items in the desired order.</span></span>

| <span data-ttu-id="a565f-109">名稱</span><span class="sxs-lookup"><span data-stu-id="a565f-109">Name</span></span>    | <span data-ttu-id="a565f-110">值</span><span class="sxs-lookup"><span data-stu-id="a565f-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a565f-111">範圍</span><span class="sxs-lookup"><span data-stu-id="a565f-111">Scope</span></span>   |<span data-ttu-id="a565f-112">透明</span><span class="sxs-lookup"><span data-stu-id="a565f-112">Transparent</span></span>|
|<span data-ttu-id="a565f-113">版本</span><span class="sxs-lookup"><span data-stu-id="a565f-113">Version</span></span>|<span data-ttu-id="a565f-114">4.5</span><span class="sxs-lookup"><span data-stu-id="a565f-114">4.5</span></span>|
|<span data-ttu-id="a565f-115">類型</span><span class="sxs-lookup"><span data-stu-id="a565f-115">Type</span></span>|<span data-ttu-id="a565f-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="a565f-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="a565f-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a565f-117">Affected APIs</span></span>

- <xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Generic.List`1.Sort``
- ``M:System.Collections.Generic.List`1.Sort(System.Collections.Generic.IComparer{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Comparison{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{`0})``

-->
