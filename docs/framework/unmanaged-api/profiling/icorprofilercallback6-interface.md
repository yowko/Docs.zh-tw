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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5025f4bb6433d193ecf7dec1d8375104147e9e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562566"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="3fb96-102">ICorProfilerCallback6 介面</span><span class="sxs-lookup"><span data-stu-id="3fb96-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="3fb96-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="3fb96-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3fb96-104">子類別[ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)提供一種回呼方法，common language runtime 用來通知分析工具在載入組件。</span><span class="sxs-lookup"><span data-stu-id="3fb96-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3fb96-105">方法</span><span class="sxs-lookup"><span data-stu-id="3fb96-105">Methods</span></span>  
  
|<span data-ttu-id="3fb96-106">方法</span><span class="sxs-lookup"><span data-stu-id="3fb96-106">Method</span></span>|<span data-ttu-id="3fb96-107">描述</span><span class="sxs-lookup"><span data-stu-id="3fb96-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3fb96-108">GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="3fb96-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="3fb96-109">當 Common Language Runtime 執行組件參考關閉查核時，通知分析工具組件處於非常早期的載入中階段。</span><span class="sxs-lookup"><span data-stu-id="3fb96-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fb96-110">備註</span><span class="sxs-lookup"><span data-stu-id="3fb96-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fb96-111">需求</span><span class="sxs-lookup"><span data-stu-id="3fb96-111">Requirements</span></span>  
 <span data-ttu-id="3fb96-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3fb96-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fb96-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3fb96-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3fb96-114">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fb96-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb96-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fb96-115">See also</span></span>
- [<span data-ttu-id="3fb96-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="3fb96-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
