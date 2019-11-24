---
title: ICorProfilerCallback::COMClassicVTableCreated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type:
- apiref
ms.openlocfilehash: 79be2572f52ec509d9551261074204bf62ad5388
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445056"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="e36fb-102">ICorProfilerCallback::COMClassicVTableCreated 方法</span><span class="sxs-lookup"><span data-stu-id="e36fb-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="e36fb-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span><span class="sxs-lookup"><span data-stu-id="e36fb-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e36fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="e36fb-104">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e36fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="e36fb-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="e36fb-106">[in] The ID of the class for which the vtable has been created.</span><span class="sxs-lookup"><span data-stu-id="e36fb-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="e36fb-107">[in] The ID of the interface implemented by the class.</span><span class="sxs-lookup"><span data-stu-id="e36fb-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="e36fb-108">This value may be NULL if the interface is internal only.</span><span class="sxs-lookup"><span data-stu-id="e36fb-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="e36fb-109">[in] A pointer to the start of the vtable.</span><span class="sxs-lookup"><span data-stu-id="e36fb-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="e36fb-110">[in] The number of slots that are in the vtable.</span><span class="sxs-lookup"><span data-stu-id="e36fb-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e36fb-111">備註</span><span class="sxs-lookup"><span data-stu-id="e36fb-111">Remarks</span></span>  
 <span data-ttu-id="e36fb-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span><span class="sxs-lookup"><span data-stu-id="e36fb-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="e36fb-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span><span class="sxs-lookup"><span data-stu-id="e36fb-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="e36fb-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span><span class="sxs-lookup"><span data-stu-id="e36fb-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e36fb-115">需求</span><span class="sxs-lookup"><span data-stu-id="e36fb-115">Requirements</span></span>  
 <span data-ttu-id="e36fb-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e36fb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e36fb-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e36fb-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e36fb-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e36fb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e36fb-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e36fb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e36fb-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="e36fb-120">See also</span></span>

- [<span data-ttu-id="e36fb-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="e36fb-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e36fb-122">COMClassicVTableDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="e36fb-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
