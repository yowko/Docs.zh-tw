---
ms.openlocfilehash: 25437dcc0c814ed2265b2efb34316af48b372ebd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497407"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="4fbaf-101">分析工具不會列舉 COR_PRF_GC_ROOT_HANDLE</span><span class="sxs-lookup"><span data-stu-id="4fbaf-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

#### <a name="details"></a><span data-ttu-id="4fbaf-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4fbaf-102">Details</span></span>

<span data-ttu-id="4fbaf-103">在 .NET Framework v4.5.1 中，分析 API <code>RootReferences2()</code> 會錯誤地永不傳回 <code>COR_PRF_GC_ROOT_HANDLE</code> (而是傳回為 <code>COR_PRF_GC_ROOT_OTHER</code>)。</span><span class="sxs-lookup"><span data-stu-id="4fbaf-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="4fbaf-104">從 .NET Framework 4.6 開始，已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="4fbaf-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4fbaf-105">建議</span><span class="sxs-lookup"><span data-stu-id="4fbaf-105">Suggestion</span></span>

<span data-ttu-id="4fbaf-106">此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="4fbaf-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="4fbaf-107">名稱</span><span class="sxs-lookup"><span data-stu-id="4fbaf-107">Name</span></span>    | <span data-ttu-id="4fbaf-108">值</span><span class="sxs-lookup"><span data-stu-id="4fbaf-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4fbaf-109">範圍</span><span class="sxs-lookup"><span data-stu-id="4fbaf-109">Scope</span></span>   |<span data-ttu-id="4fbaf-110">Minor</span><span class="sxs-lookup"><span data-stu-id="4fbaf-110">Minor</span></span>|
|<span data-ttu-id="4fbaf-111">版本</span><span class="sxs-lookup"><span data-stu-id="4fbaf-111">Version</span></span>|<span data-ttu-id="4fbaf-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="4fbaf-112">4.5.1</span></span>|
|<span data-ttu-id="4fbaf-113">類型</span><span class="sxs-lookup"><span data-stu-id="4fbaf-113">Type</span></span>|<span data-ttu-id="4fbaf-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="4fbaf-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4fbaf-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4fbaf-115">Affected APIs</span></span>

<span data-ttu-id="4fbaf-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="4fbaf-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
