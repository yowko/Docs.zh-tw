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
ms.openlocfilehash: 2325e3034dbf00441e587017affa65b80821fbb1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128757"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="c6273-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 方法</span><span class="sxs-lookup"><span data-stu-id="c6273-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="c6273-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="c6273-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c6273-104">通知 common language runtime （CLR）程式碼剖析工具計畫要在[ICorProfilerCallback：： ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼中新增的元件參考。</span><span class="sxs-lookup"><span data-stu-id="c6273-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6273-105">語法</span><span class="sxs-lookup"><span data-stu-id="c6273-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6273-106">參數</span><span class="sxs-lookup"><span data-stu-id="c6273-106">Parameters</span></span>  
 <span data-ttu-id="c6273-107">pAssemblyRefInfo</span><span class="sxs-lookup"><span data-stu-id="c6273-107">pAssemblyRefInfo</span></span>  
 <span data-ttu-id="c6273-108">[COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)結構的指標，提供 CLR 在執行元件參考關閉行程時應考慮之元件參考的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c6273-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6273-109">備註</span><span class="sxs-lookup"><span data-stu-id="c6273-109">Remarks</span></span>  
 <span data-ttu-id="c6273-110">分析工具會針對其計畫從[ICorProfilerCallback6：： GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼的 `wszAssemblyPath` 引數中指定的元件來參考的每個目標群組件，呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="c6273-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="c6273-111">[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)介面物件會傳遞至分析工具的[ICorProfilerCallback6：： GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼，以及 `wszAssemblyPath` 引數中的元件路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="c6273-111">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6273-112">需求</span><span class="sxs-lookup"><span data-stu-id="c6273-112">Requirements</span></span>  
 <span data-ttu-id="c6273-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6273-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6273-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c6273-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6273-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6273-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6273-116">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6273-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6273-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="c6273-117">See also</span></span>

- [<span data-ttu-id="c6273-118">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="c6273-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="c6273-119">GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="c6273-119">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="c6273-120">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="c6273-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
