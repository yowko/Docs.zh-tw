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
ms.openlocfilehash: 05e571149a794cbffa9e602255455d779a83e2a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452952"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="f6f06-102">ICorProfilerCallback6 介面</span><span class="sxs-lookup"><span data-stu-id="f6f06-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="f6f06-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="f6f06-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f6f06-104">子類別[ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)提供 common language runtime 用於通知分析工具組件載入的回撥方法。</span><span class="sxs-lookup"><span data-stu-id="f6f06-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6f06-105">方法</span><span class="sxs-lookup"><span data-stu-id="f6f06-105">Methods</span></span>  
  
|<span data-ttu-id="f6f06-106">方法</span><span class="sxs-lookup"><span data-stu-id="f6f06-106">Method</span></span>|<span data-ttu-id="f6f06-107">描述</span><span class="sxs-lookup"><span data-stu-id="f6f06-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6f06-108">GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="f6f06-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="f6f06-109">當 Common Language Runtime 執行組件參考關閉查核時，通知分析工具組件處於非常早期的載入中階段。</span><span class="sxs-lookup"><span data-stu-id="f6f06-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6f06-110">備註</span><span class="sxs-lookup"><span data-stu-id="f6f06-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6f06-111">需求</span><span class="sxs-lookup"><span data-stu-id="f6f06-111">Requirements</span></span>  
 <span data-ttu-id="f6f06-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6f06-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6f06-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f6f06-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f6f06-114">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6f06-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f06-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6f06-115">See Also</span></span>  
 [<span data-ttu-id="f6f06-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="f6f06-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
