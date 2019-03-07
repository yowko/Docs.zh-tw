---
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae7d896ee8e06921d685fad9ae2fcc0ac215d64a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485053"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="061cd-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 方法</span><span class="sxs-lookup"><span data-stu-id="061cd-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="061cd-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="061cd-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="061cd-104">通知分析工具計劃要加入的組件參考 common language runtime (CLR) [icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="061cd-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="061cd-105">語法</span><span class="sxs-lookup"><span data-stu-id="061cd-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="061cd-106">參數</span><span class="sxs-lookup"><span data-stu-id="061cd-106">Parameters</span></span>  
 <span data-ttu-id="061cd-107">pAssemblyRefInfo</span><span class="sxs-lookup"><span data-stu-id="061cd-107">pAssemblyRefInfo</span></span>  
 <span data-ttu-id="061cd-108">指標[COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)提供 CLR 組件參考所執行的組件參考結束查核時應考量的相關資訊的結構。</span><span class="sxs-lookup"><span data-stu-id="061cd-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="061cd-109">備註</span><span class="sxs-lookup"><span data-stu-id="061cd-109">Remarks</span></span>  
 <span data-ttu-id="061cd-110">分析工具會呼叫這個方法，每個目標組件計劃要從指定的組件參考`wszAssemblyPath`引數[ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="061cd-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="061cd-111">[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)介面的物件會傳遞至分析工具的[ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼，以及組件路徑和名稱`wszAssemblyPath`引數。</span><span class="sxs-lookup"><span data-stu-id="061cd-111">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="061cd-112">需求</span><span class="sxs-lookup"><span data-stu-id="061cd-112">Requirements</span></span>  
 <span data-ttu-id="061cd-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="061cd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="061cd-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="061cd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="061cd-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="061cd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="061cd-116">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="061cd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="061cd-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="061cd-117">See also</span></span>
- [<span data-ttu-id="061cd-118">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="061cd-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="061cd-119">GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="061cd-119">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="061cd-120">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="061cd-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
