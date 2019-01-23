---
title: ICorProfilerAssemblyReferenceProvider 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65c18f534771407b2dcf4710e2604e0b30cbdcdb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611042"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="0ebb1-102">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="0ebb1-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="0ebb1-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="0ebb1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0ebb1-104">可讓分析工具通知分析工具會在加入的組件參考的 common language runtime (CLR) [icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="0ebb1-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ebb1-105">方法</span><span class="sxs-lookup"><span data-stu-id="0ebb1-105">Methods</span></span>  
  
|<span data-ttu-id="0ebb1-106">方法</span><span class="sxs-lookup"><span data-stu-id="0ebb1-106">Method</span></span>|<span data-ttu-id="0ebb1-107">描述</span><span class="sxs-lookup"><span data-stu-id="0ebb1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ebb1-108">AddAssemblyReference 方法</span><span class="sxs-lookup"><span data-stu-id="0ebb1-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="0ebb1-109">通知分析工具計劃要在加入的組件參考的 CLR [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="0ebb1-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ebb1-110">備註</span><span class="sxs-lookup"><span data-stu-id="0ebb1-110">Remarks</span></span>  
 <span data-ttu-id="0ebb1-111">CLR 會傳遞分析工具`ICorProfilerAssemblyReferenceProvider`介面中的物件[ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="0ebb1-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="0ebb1-112">這可讓分析工具通知分析工具計劃要在稍後加入的組件參考的 CLR [icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0ebb1-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="0ebb1-113">回呼中。</span><span class="sxs-lookup"><span data-stu-id="0ebb1-113">callback.</span></span> <span data-ttu-id="0ebb1-114">這會增進 CLR 組件參考結束查核器及其演算法的精確度，以判定組件是否可以共用。</span><span class="sxs-lookup"><span data-stu-id="0ebb1-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="0ebb1-115">只有在無法使用此介面[ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)這個介面會將物件傳遞至分析工具的回呼。</span><span class="sxs-lookup"><span data-stu-id="0ebb1-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ebb1-116">需求</span><span class="sxs-lookup"><span data-stu-id="0ebb1-116">Requirements</span></span>  
 <span data-ttu-id="0ebb1-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ebb1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ebb1-118">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0ebb1-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0ebb1-119">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ebb1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ebb1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ebb1-120">See also</span></span>
- [<span data-ttu-id="0ebb1-121">分析介面</span><span class="sxs-lookup"><span data-stu-id="0ebb1-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
