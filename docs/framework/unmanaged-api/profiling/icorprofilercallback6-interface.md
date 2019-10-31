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
ms.openlocfilehash: 0009d935e2e3b2abf590aca270113717ceb7e2d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127475"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="93298-102">ICorProfilerCallback6 介面</span><span class="sxs-lookup"><span data-stu-id="93298-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="93298-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="93298-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="93298-104">[ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)的子類別，提供通用語言執行時間用來通知分析工具元件正在載入的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="93298-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93298-105">方法</span><span class="sxs-lookup"><span data-stu-id="93298-105">Methods</span></span>  
  
|<span data-ttu-id="93298-106">方法</span><span class="sxs-lookup"><span data-stu-id="93298-106">Method</span></span>|<span data-ttu-id="93298-107">描述</span><span class="sxs-lookup"><span data-stu-id="93298-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93298-108">GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="93298-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="93298-109">當 Common Language Runtime 執行組件參考關閉查核時，通知分析工具組件處於非常早期的載入中階段。</span><span class="sxs-lookup"><span data-stu-id="93298-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93298-110">備註</span><span class="sxs-lookup"><span data-stu-id="93298-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93298-111">需求</span><span class="sxs-lookup"><span data-stu-id="93298-111">Requirements</span></span>  
 <span data-ttu-id="93298-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93298-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93298-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="93298-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93298-114">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93298-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93298-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="93298-115">See also</span></span>

- [<span data-ttu-id="93298-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="93298-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
