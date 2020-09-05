---
ms.openlocfilehash: af8de731ee93d0bfb01042d894f5730570dcdd78
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496621"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="5d862-101">在稍後的步驟中，偵錯工具才會顯示 Null 聯合器值</span><span class="sxs-lookup"><span data-stu-id="5d862-101">Null coalescer values are not visible in debugger until one step later</span></span>

#### <a name="details"></a><span data-ttu-id="5d862-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5d862-102">Details</span></span>

<span data-ttu-id="5d862-103">.NET Framework 4.5 中的 Bug) 會導致在 64 位元版本的 Framework 上執行時，透過 Null 聯合運算設定的值不會立即於執行指派作業之後顯示在偵錯工具中。</span><span class="sxs-lookup"><span data-stu-id="5d862-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5d862-104">建議</span><span class="sxs-lookup"><span data-stu-id="5d862-104">Suggestion</span></span>

<span data-ttu-id="5d862-105">在偵錯工具中逐步執行一段額外時間，將使本機/欄位的值正確更新。</span><span class="sxs-lookup"><span data-stu-id="5d862-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="5d862-106">此外，此問題已在 .NET Framework 4.6 中修正；升級至該版 .NET Framework 應可解決此問題。</span><span class="sxs-lookup"><span data-stu-id="5d862-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>

| <span data-ttu-id="5d862-107">名稱</span><span class="sxs-lookup"><span data-stu-id="5d862-107">Name</span></span>    | <span data-ttu-id="5d862-108">值</span><span class="sxs-lookup"><span data-stu-id="5d862-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5d862-109">範圍</span><span class="sxs-lookup"><span data-stu-id="5d862-109">Scope</span></span>   |<span data-ttu-id="5d862-110">Edge</span><span class="sxs-lookup"><span data-stu-id="5d862-110">Edge</span></span>|
|<span data-ttu-id="5d862-111">版本</span><span class="sxs-lookup"><span data-stu-id="5d862-111">Version</span></span>|<span data-ttu-id="5d862-112">4.5</span><span class="sxs-lookup"><span data-stu-id="5d862-112">4.5</span></span>|
|<span data-ttu-id="5d862-113">類型</span><span class="sxs-lookup"><span data-stu-id="5d862-113">Type</span></span>|<span data-ttu-id="5d862-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="5d862-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5d862-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5d862-115">Affected APIs</span></span>

<span data-ttu-id="5d862-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="5d862-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
