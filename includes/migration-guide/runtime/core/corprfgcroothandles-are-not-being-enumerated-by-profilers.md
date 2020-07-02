---
ms.openlocfilehash: 4f52535e54607cc824500f9c6a14964a1dec9d32
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619958"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="28a7e-101">分析工具不會列舉 COR_PRF_GC_ROOT_HANDLE</span><span class="sxs-lookup"><span data-stu-id="28a7e-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

#### <a name="details"></a><span data-ttu-id="28a7e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="28a7e-102">Details</span></span>

<span data-ttu-id="28a7e-103">在 .NET Framework v4.5.1 中，分析 API <code>RootReferences2()</code> 會錯誤地永不傳回 <code>COR_PRF_GC_ROOT_HANDLE</code> (而是傳回為 <code>COR_PRF_GC_ROOT_OTHER</code>)。</span><span class="sxs-lookup"><span data-stu-id="28a7e-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="28a7e-104">從 .NET Framework 4.6 開始，已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="28a7e-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="28a7e-105">建議</span><span class="sxs-lookup"><span data-stu-id="28a7e-105">Suggestion</span></span>

<span data-ttu-id="28a7e-106">此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="28a7e-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="28a7e-107">名稱</span><span class="sxs-lookup"><span data-stu-id="28a7e-107">Name</span></span>    | <span data-ttu-id="28a7e-108">值</span><span class="sxs-lookup"><span data-stu-id="28a7e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="28a7e-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="28a7e-109">Scope</span></span>   |<span data-ttu-id="28a7e-110">Minor</span><span class="sxs-lookup"><span data-stu-id="28a7e-110">Minor</span></span>|
|<span data-ttu-id="28a7e-111">版本</span><span class="sxs-lookup"><span data-stu-id="28a7e-111">Version</span></span>|<span data-ttu-id="28a7e-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="28a7e-112">4.5.1</span></span>|
|<span data-ttu-id="28a7e-113">類型</span><span class="sxs-lookup"><span data-stu-id="28a7e-113">Type</span></span>|<span data-ttu-id="28a7e-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="28a7e-114">Runtime</span></span>|
