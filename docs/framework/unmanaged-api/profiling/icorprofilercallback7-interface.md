---
title: "ICorProfilerCallback7 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8eb370e4f16212c536c252661163b7eca6f74d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="c4fc6-102">ICorProfilerCallback7 介面</span><span class="sxs-lookup"><span data-stu-id="c4fc6-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="c4fc6-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="c4fc6-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="c4fc6-104">[ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) 子類別提供一種回呼方法，以讓 Common Language Runtime 用來通知分析工具已更新記憶體中模組相關聯的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="c4fc6-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4fc6-105">方法</span><span class="sxs-lookup"><span data-stu-id="c4fc6-105">Methods</span></span>  
  
|<span data-ttu-id="c4fc6-106">方法</span><span class="sxs-lookup"><span data-stu-id="c4fc6-106">Method</span></span>|<span data-ttu-id="c4fc6-107">說明</span><span class="sxs-lookup"><span data-stu-id="c4fc6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4fc6-108">ModuleInMemorySymbolsUpdated 方法</span><span class="sxs-lookup"><span data-stu-id="c4fc6-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="c4fc6-109">通知分析工具已更新記憶體中模組相關聯的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="c4fc6-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c4fc6-110">需求</span><span class="sxs-lookup"><span data-stu-id="c4fc6-110">Requirements</span></span>  
 <span data-ttu-id="c4fc6-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fc6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4fc6-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c4fc6-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4fc6-113">**.NET framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4fc6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4fc6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4fc6-114">See Also</span></span>  
 [<span data-ttu-id="c4fc6-115">分析介面</span><span class="sxs-lookup"><span data-stu-id="c4fc6-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
