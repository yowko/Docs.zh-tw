---
title: "ICorProfilerAssemblyReferenceProvider 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerAssemblyReferenceProvider
api_location: mscorwks.dll
api_type: COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2120e400d4ecd23c86cdae7b12d8706b35e8ca08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="d2f5d-102">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="d2f5d-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="d2f5d-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="d2f5d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d2f5d-104">可讓分析工具通知分析工具會在中加入的組件參考的 common language runtime (CLR) [icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2f5d-105">方法</span><span class="sxs-lookup"><span data-stu-id="d2f5d-105">Methods</span></span>  
  
|<span data-ttu-id="d2f5d-106">方法</span><span class="sxs-lookup"><span data-stu-id="d2f5d-106">Method</span></span>|<span data-ttu-id="d2f5d-107">說明</span><span class="sxs-lookup"><span data-stu-id="d2f5d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2f5d-108">AddAssemblyReference 方法</span><span class="sxs-lookup"><span data-stu-id="d2f5d-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="d2f5d-109">通知分析工具計劃要在加入的組件參考的 CLR [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2f5d-110">備註</span><span class="sxs-lookup"><span data-stu-id="d2f5d-110">Remarks</span></span>  
 <span data-ttu-id="d2f5d-111">CLR 會傳遞分析工具`ICorProfilerAssemblyReferenceProvider`介面中的物件[icorprofilercallback6:: Getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="d2f5d-112">這可讓分析工具通知分析工具計劃要在稍後加入的組件參考的 CLR [icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="d2f5d-113">回呼中。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-113">callback.</span></span> <span data-ttu-id="d2f5d-114">這會增進 CLR 組件參考結束查核器及其演算法的精確度，以判定組件是否可以共用。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="d2f5d-115">這個介面可以只能用在[icorprofilercallback6:: Getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)將此介面物件傳遞至分析工具回呼。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2f5d-116">需求</span><span class="sxs-lookup"><span data-stu-id="d2f5d-116">Requirements</span></span>  
 <span data-ttu-id="d2f5d-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2f5d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2f5d-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d2f5d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d2f5d-119">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2f5d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f5d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2f5d-120">See Also</span></span>  
 [<span data-ttu-id="d2f5d-121">分析介面</span><span class="sxs-lookup"><span data-stu-id="d2f5d-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
