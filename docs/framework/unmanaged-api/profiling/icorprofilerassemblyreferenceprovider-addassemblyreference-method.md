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
ms.openlocfilehash: 6d732c6c2871cc5e042b8504db26aabb19963f8c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500503"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="8b6c0-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 方法</span><span class="sxs-lookup"><span data-stu-id="8b6c0-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="8b6c0-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="8b6c0-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8b6c0-104">通知 common language runtime （CLR）程式碼剖析工具計畫要在[ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回呼中新增的元件參考。</span><span class="sxs-lookup"><span data-stu-id="8b6c0-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b6c0-105">語法</span><span class="sxs-lookup"><span data-stu-id="8b6c0-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b6c0-106">參數</span><span class="sxs-lookup"><span data-stu-id="8b6c0-106">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="8b6c0-107">[COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md)結構的指標，為 CLR 提供在執行元件參考關閉行程時，應該考慮之元件參考的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8b6c0-107">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="8b6c0-108">備註</span><span class="sxs-lookup"><span data-stu-id="8b6c0-108">Remarks</span></span>  
 <span data-ttu-id="8b6c0-109">分析工具會針對其計畫從 `wszAssemblyPath` [ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回呼的引數中指定的元件來參考的每個目標群組件，呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="8b6c0-109">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="8b6c0-110">[ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)介面物件會傳遞至分析工具的[ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回呼，以及引數中的元件路徑和名稱 `wszAssemblyPath` 。</span><span class="sxs-lookup"><span data-stu-id="8b6c0-110">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b6c0-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="8b6c0-111">Requirements</span></span>  
 <span data-ttu-id="8b6c0-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b6c0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b6c0-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b6c0-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b6c0-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b6c0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b6c0-115">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b6c0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b6c0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b6c0-116">See also</span></span>

- [<span data-ttu-id="8b6c0-117">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="8b6c0-117">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="8b6c0-118">GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="8b6c0-118">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="8b6c0-119">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="8b6c0-119">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
