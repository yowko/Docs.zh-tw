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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9f5d2c08abbcab6bc1a6d0569b8e70d7c919def
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195861"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="982a7-102">ICorProfilerCallback::ObjectsAllocatedByClass 方法</span><span class="sxs-lookup"><span data-stu-id="982a7-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="982a7-103">通知分析工具有關的每個指定的類別已自最新的回收之後建立的執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="982a7-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="982a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="982a7-104">Syntax</span></span>  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="982a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="982a7-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="982a7-106">[in]大小`classIds`和`cObjects`陣列。</span><span class="sxs-lookup"><span data-stu-id="982a7-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="982a7-107">[in]類別識別碼，其中每個識別碼指定的類別與一或多個執行個體的陣列。</span><span class="sxs-lookup"><span data-stu-id="982a7-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="982a7-108">[in]整數，指定每個整數中的對應類別的執行個體數目的陣列`classIds`陣列。</span><span class="sxs-lookup"><span data-stu-id="982a7-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="982a7-109">備註</span><span class="sxs-lookup"><span data-stu-id="982a7-109">Remarks</span></span>  
 <span data-ttu-id="982a7-110">`classIds`和`cObjects`陣列是平行陣列。</span><span class="sxs-lookup"><span data-stu-id="982a7-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="982a7-111">例如，`classIds[i]`和`cObjects[i]`參考相同的類別。</span><span class="sxs-lookup"><span data-stu-id="982a7-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="982a7-112">如果自上一個記憶體回收之後建立的類別執行個體之後，即會省略的類別。</span><span class="sxs-lookup"><span data-stu-id="982a7-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="982a7-113">`ObjectsAllocatedByClass`回呼將不會報告在大型物件堆積中配置的物件。</span><span class="sxs-lookup"><span data-stu-id="982a7-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="982a7-114">所報告的數字`ObjectsAllocatedByClass`是只是估計值。</span><span class="sxs-lookup"><span data-stu-id="982a7-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="982a7-115">確切的計數，請使用[icorprofilercallback:: Objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)。</span><span class="sxs-lookup"><span data-stu-id="982a7-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="982a7-116">`classIds`陣列可能包含一或多個 null 的項目，如果對應`cObjects`陣列有要卸載的類型。</span><span class="sxs-lookup"><span data-stu-id="982a7-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="982a7-117">需求</span><span class="sxs-lookup"><span data-stu-id="982a7-117">Requirements</span></span>  
 <span data-ttu-id="982a7-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="982a7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="982a7-119">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="982a7-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="982a7-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="982a7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="982a7-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="982a7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="982a7-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="982a7-122">See also</span></span>

- [<span data-ttu-id="982a7-123">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="982a7-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
