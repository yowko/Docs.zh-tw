---
title: "ICorProfilerCallback::ObjectsAllocatedByClass 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectsAllocatedByClass
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 28c0ff537a5b2133bdeb1db8aeadf5545d8dfd0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="88c83-102">ICorProfilerCallback::ObjectsAllocatedByClass 方法</span><span class="sxs-lookup"><span data-stu-id="88c83-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="88c83-103">通知分析工具有關的每個指定的類別已建立最新的記憶體回收回收後的執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="88c83-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88c83-104">語法</span><span class="sxs-lookup"><span data-stu-id="88c83-104">Syntax</span></span>  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88c83-105">參數</span><span class="sxs-lookup"><span data-stu-id="88c83-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="88c83-106">[in]大小`classIds`和`cObjects`陣列。</span><span class="sxs-lookup"><span data-stu-id="88c83-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="88c83-107">[in]陣列的類別識別碼，其中每個識別碼與一或多個執行個體中指定的類別。</span><span class="sxs-lookup"><span data-stu-id="88c83-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="88c83-108">[in]整數，指定每個整數的中的對應類別執行個體數目的陣列`classIds`陣列。</span><span class="sxs-lookup"><span data-stu-id="88c83-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88c83-109">備註</span><span class="sxs-lookup"><span data-stu-id="88c83-109">Remarks</span></span>  
 <span data-ttu-id="88c83-110">`classIds`和`cObjects`是平行陣列。</span><span class="sxs-lookup"><span data-stu-id="88c83-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="88c83-111">例如，`classIds[i]`和`cObjects[i]`參考相同的類別。</span><span class="sxs-lookup"><span data-stu-id="88c83-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="88c83-112">自上一個記憶體回收之後建立的類別執行個體之後，如果省略，則此類別。</span><span class="sxs-lookup"><span data-stu-id="88c83-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="88c83-113">`ObjectsAllocatedByClass`回呼不會報告在大型物件堆積中配置的物件。</span><span class="sxs-lookup"><span data-stu-id="88c83-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="88c83-114">所報告的數字`ObjectsAllocatedByClass`都只是估計值。</span><span class="sxs-lookup"><span data-stu-id="88c83-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="88c83-115">確切計數，使用[icorprofilercallback:: Objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)。</span><span class="sxs-lookup"><span data-stu-id="88c83-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="88c83-116">`classIds`陣列可能包含一或多個 null 項目，如果對應`cObjects`陣列有要卸載的類型。</span><span class="sxs-lookup"><span data-stu-id="88c83-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88c83-117">需求</span><span class="sxs-lookup"><span data-stu-id="88c83-117">Requirements</span></span>  
 <span data-ttu-id="88c83-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="88c83-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88c83-119">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="88c83-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="88c83-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88c83-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88c83-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88c83-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88c83-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88c83-122">See Also</span></span>  
 [<span data-ttu-id="88c83-123">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="88c83-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
