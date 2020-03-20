---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858521"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="e8156-101">分析工具不會列舉 COR_PRF_GC_ROOT_HANDLE</span><span class="sxs-lookup"><span data-stu-id="e8156-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e8156-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e8156-102">Details</span></span>|<span data-ttu-id="e8156-103">在 .NET Framework v4.5.1 中，分析 API <code>RootReferences2()</code> 會錯誤地永不傳回 <code>COR_PRF_GC_ROOT_HANDLE</code> (而是傳回為 <code>COR_PRF_GC_ROOT_OTHER</code>)。</span><span class="sxs-lookup"><span data-stu-id="e8156-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="e8156-104">從 .NET Framework 4.6 開始，已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="e8156-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="e8156-105">建議</span><span class="sxs-lookup"><span data-stu-id="e8156-105">Suggestion</span></span>|<span data-ttu-id="e8156-106">此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="e8156-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="e8156-107">影響範圍</span><span class="sxs-lookup"><span data-stu-id="e8156-107">Scope</span></span>|<span data-ttu-id="e8156-108">Minor</span><span class="sxs-lookup"><span data-stu-id="e8156-108">Minor</span></span>|
|<span data-ttu-id="e8156-109">版本</span><span class="sxs-lookup"><span data-stu-id="e8156-109">Version</span></span>|<span data-ttu-id="e8156-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="e8156-110">4.5.1</span></span>|
|<span data-ttu-id="e8156-111">類型</span><span class="sxs-lookup"><span data-stu-id="e8156-111">Type</span></span>|<span data-ttu-id="e8156-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="e8156-112">Runtime</span></span>|
