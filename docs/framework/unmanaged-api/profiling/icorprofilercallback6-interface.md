---
title: ICorProfilerCallback6 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
ms.openlocfilehash: 90071121411b706052e1cbb4cb647536dae2835a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864865"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="d0a30-102">ICorProfilerCallback6 介面</span><span class="sxs-lookup"><span data-stu-id="d0a30-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="d0a30-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="d0a30-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d0a30-104">[ICorProfilerCallback5](icorprofilercallback5-interface.md)的子類別，提供通用語言執行時間用來通知分析工具元件正在載入的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="d0a30-104">A subclass of [ICorProfilerCallback5](icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0a30-105">方法</span><span class="sxs-lookup"><span data-stu-id="d0a30-105">Methods</span></span>  
  
|<span data-ttu-id="d0a30-106">方法</span><span class="sxs-lookup"><span data-stu-id="d0a30-106">Method</span></span>|<span data-ttu-id="d0a30-107">描述</span><span class="sxs-lookup"><span data-stu-id="d0a30-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0a30-108">GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="d0a30-108">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="d0a30-109">當 Common Language Runtime 執行組件參考關閉查核時，通知分析工具組件處於非常早期的載入中階段。</span><span class="sxs-lookup"><span data-stu-id="d0a30-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0a30-110">備註</span><span class="sxs-lookup"><span data-stu-id="d0a30-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0a30-111">需求</span><span class="sxs-lookup"><span data-stu-id="d0a30-111">Requirements</span></span>  
 <span data-ttu-id="d0a30-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0a30-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0a30-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d0a30-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d0a30-114">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0a30-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a30-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d0a30-115">See also</span></span>

- [<span data-ttu-id="d0a30-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="d0a30-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
