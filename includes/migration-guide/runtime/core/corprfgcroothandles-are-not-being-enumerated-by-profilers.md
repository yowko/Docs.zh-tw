---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235127"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="6aeaa-101">分析工具不會列舉 COR_PRF_GC_ROOT_HANDLE</span><span class="sxs-lookup"><span data-stu-id="6aeaa-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6aeaa-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6aeaa-102">Details</span></span>|<span data-ttu-id="6aeaa-103">在 .NET Framework v4.5.1 中，分析 API <code>RootReferences2()</code> 會錯誤地永不傳回 <code>COR_PRF_GC_ROOT_HANDLE</code> (而是傳回為 <code>COR_PRF_GC_ROOT_OTHER</code>)。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="6aeaa-104">從 .NET Framework 4.6 開始，已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="6aeaa-105">建議</span><span class="sxs-lookup"><span data-stu-id="6aeaa-105">Suggestion</span></span>|<span data-ttu-id="6aeaa-106">此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="6aeaa-107">範圍</span><span class="sxs-lookup"><span data-stu-id="6aeaa-107">Scope</span></span>|<span data-ttu-id="6aeaa-108">次要</span><span class="sxs-lookup"><span data-stu-id="6aeaa-108">Minor</span></span>|
|<span data-ttu-id="6aeaa-109">版本</span><span class="sxs-lookup"><span data-stu-id="6aeaa-109">Version</span></span>|<span data-ttu-id="6aeaa-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="6aeaa-110">4.5.1</span></span>|
|<span data-ttu-id="6aeaa-111">類型</span><span class="sxs-lookup"><span data-stu-id="6aeaa-111">Type</span></span>|<span data-ttu-id="6aeaa-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="6aeaa-112">Runtime</span></span>|
