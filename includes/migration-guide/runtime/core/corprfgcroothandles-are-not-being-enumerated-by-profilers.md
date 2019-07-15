---
ms.openlocfilehash: 8dc98b2d9c2c0b5f145ebce48cf8f5e054975c6e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858521"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="d6065-101">分析工具不會列舉 COR_PRF_GC_ROOT_HANDLE</span><span class="sxs-lookup"><span data-stu-id="d6065-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d6065-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d6065-102">Details</span></span>|<span data-ttu-id="d6065-103">在 .NET Framework v4.5.1 中，分析 API <code>RootReferences2()</code> 會錯誤地永不傳回 <code>COR_PRF_GC_ROOT_HANDLE</code> (而是傳回為 <code>COR_PRF_GC_ROOT_OTHER</code>)。</span><span class="sxs-lookup"><span data-stu-id="d6065-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="d6065-104">從 .NET Framework 4.6 開始，已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="d6065-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="d6065-105">建議</span><span class="sxs-lookup"><span data-stu-id="d6065-105">Suggestion</span></span>|<span data-ttu-id="d6065-106">此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="d6065-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="d6065-107">範圍</span><span class="sxs-lookup"><span data-stu-id="d6065-107">Scope</span></span>|<span data-ttu-id="d6065-108">次要</span><span class="sxs-lookup"><span data-stu-id="d6065-108">Minor</span></span>|
|<span data-ttu-id="d6065-109">版本</span><span class="sxs-lookup"><span data-stu-id="d6065-109">Version</span></span>|<span data-ttu-id="d6065-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d6065-110">4.5.1</span></span>|
|<span data-ttu-id="d6065-111">類型</span><span class="sxs-lookup"><span data-stu-id="d6065-111">Type</span></span>|<span data-ttu-id="d6065-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="d6065-112">Runtime</span></span>|

