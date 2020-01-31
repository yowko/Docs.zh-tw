---
title: ICorProfilerCallback::ObjectsAllocatedByClass 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
ms.openlocfilehash: 028207486f43e35086ed2e515eb3ae6bca304491
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866068"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="6f450-102">ICorProfilerCallback::ObjectsAllocatedByClass 方法</span><span class="sxs-lookup"><span data-stu-id="6f450-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="6f450-103">通知分析工具關於最近一次垃圾收集之後所建立之每個指定類別的實例數目。</span><span class="sxs-lookup"><span data-stu-id="6f450-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f450-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f450-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f450-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f450-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="6f450-106">在`classIds` 和 `cObjects` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="6f450-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="6f450-107">在類別識別碼的陣列，其中的每個識別碼會指定具有一或多個實例的類別。</span><span class="sxs-lookup"><span data-stu-id="6f450-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="6f450-108">在整數的陣列，其中每個整數會指定 `classIds` 陣列中對應類別的實例數目。</span><span class="sxs-lookup"><span data-stu-id="6f450-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f450-109">備註</span><span class="sxs-lookup"><span data-stu-id="6f450-109">Remarks</span></span>  
 <span data-ttu-id="6f450-110">`classIds` 和 `cObjects` 陣列是平行陣列。</span><span class="sxs-lookup"><span data-stu-id="6f450-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="6f450-111">例如，`classIds[i]` 和 `cObjects[i]` 參考相同的類別。</span><span class="sxs-lookup"><span data-stu-id="6f450-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="6f450-112">如果自從上一次垃圾收集之後，尚未建立類別的實例，則會省略類別。</span><span class="sxs-lookup"><span data-stu-id="6f450-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="6f450-113">`ObjectsAllocatedByClass` 回呼不會報告在大型物件堆積中所配置的物件。</span><span class="sxs-lookup"><span data-stu-id="6f450-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="6f450-114">`ObjectsAllocatedByClass` 回報的數位僅供估計。</span><span class="sxs-lookup"><span data-stu-id="6f450-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="6f450-115">如需確切計數，請使用[ICorProfilerCallback：： ObjectAllocated](icorprofilercallback-objectallocated-method.md)。</span><span class="sxs-lookup"><span data-stu-id="6f450-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="6f450-116">如果對應的 `cObjects` 陣列具有正在卸載的類型，`classIds` 陣列可能會包含一或多個 null 專案。</span><span class="sxs-lookup"><span data-stu-id="6f450-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f450-117">需求</span><span class="sxs-lookup"><span data-stu-id="6f450-117">Requirements</span></span>  
 <span data-ttu-id="6f450-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f450-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f450-119">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f450-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f450-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f450-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f450-121">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f450-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f450-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="6f450-122">See also</span></span>

- [<span data-ttu-id="6f450-123">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6f450-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
