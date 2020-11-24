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
ms.openlocfilehash: 56468fd38bc110318e04d9b1beda61e279f731d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685316"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="777b3-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 方法</span><span class="sxs-lookup"><span data-stu-id="777b3-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>

<span data-ttu-id="777b3-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="777b3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="777b3-104">通知 common language runtime (CLR) 程式碼剖析工具計畫在 [ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 回呼中加入的元件參考。</span><span class="sxs-lookup"><span data-stu-id="777b3-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="777b3-105">語法</span><span class="sxs-lookup"><span data-stu-id="777b3-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="777b3-106">參數</span><span class="sxs-lookup"><span data-stu-id="777b3-106">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="777b3-107">[COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md)結構的指標，此結構會為 CLR 提供元件參考的相關資訊，以便在執行元件參考結束時進行考慮。</span><span class="sxs-lookup"><span data-stu-id="777b3-107">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="777b3-108">備註</span><span class="sxs-lookup"><span data-stu-id="777b3-108">Remarks</span></span>  

 <span data-ttu-id="777b3-109">分析工具會針對其計畫從 `wszAssemblyPath` [ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) 回呼的引數中指定的元件參考的每個目標群組件，呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="777b3-109">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="777b3-110">[ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)介面物件會傳遞至分析工具的[ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)回呼，以及引數中的元件路徑和名稱 `wszAssemblyPath` 。</span><span class="sxs-lookup"><span data-stu-id="777b3-110">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="777b3-111">需求</span><span class="sxs-lookup"><span data-stu-id="777b3-111">Requirements</span></span>  

 <span data-ttu-id="777b3-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="777b3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="777b3-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="777b3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="777b3-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="777b3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="777b3-115">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="777b3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="777b3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="777b3-116">See also</span></span>

- [<span data-ttu-id="777b3-117">ICorProfilerAssemblyReferenceProvider 介面</span><span class="sxs-lookup"><span data-stu-id="777b3-117">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="777b3-118">GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="777b3-118">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="777b3-119">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="777b3-119">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
