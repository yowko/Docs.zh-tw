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
ms.openlocfilehash: 70d43d7526376c40d0f8358ebd65e4a00a41b969
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701662"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="dbb3e-102">ICorProfilerCallback::ObjectsAllocatedByClass 方法</span><span class="sxs-lookup"><span data-stu-id="dbb3e-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>

<span data-ttu-id="dbb3e-103">通知分析工具有關最近一次垃圾收集之後所建立之每個指定類別的實例數目。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbb3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbb3e-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbb3e-105">參數</span><span class="sxs-lookup"><span data-stu-id="dbb3e-105">Parameters</span></span>  

 `cClassCount`  
 <span data-ttu-id="dbb3e-106">在和陣列的大小 `classIds` `cObjects` 。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="dbb3e-107">在類別識別碼的陣列，其中每個識別碼都會指定具有一或多個實例的類別。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="dbb3e-108">在整數陣列，其中每個整數會指定陣列中對應類別的實例數目 `classIds` 。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbb3e-109">備註</span><span class="sxs-lookup"><span data-stu-id="dbb3e-109">Remarks</span></span>  

 <span data-ttu-id="dbb3e-110">`classIds`和 `cObjects` 陣列是平行陣列。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="dbb3e-111">例如， `classIds[i]` 和 `cObjects[i]` 參考相同的類別。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="dbb3e-112">如果自上一次垃圾收集之後未建立類別的實例，則會省略類別。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="dbb3e-113">`ObjectsAllocatedByClass`回呼不會報告大型物件堆積中所配置的物件。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="dbb3e-114">所報告的數位 `ObjectsAllocatedByClass` 只會預估。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="dbb3e-115">針對確切計數，請使用 [ICorProfilerCallback：： ObjectAllocated](icorprofilercallback-objectallocated-method.md)。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="dbb3e-116">`classIds`如果對應的 `cObjects` 陣列具有正在卸載的型別，陣列可能會包含一個或多個 null 專案。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbb3e-117">需求</span><span class="sxs-lookup"><span data-stu-id="dbb3e-117">Requirements</span></span>  

 <span data-ttu-id="dbb3e-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbb3e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbb3e-119">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dbb3e-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dbb3e-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbb3e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbb3e-121">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbb3e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbb3e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbb3e-122">See also</span></span>

- [<span data-ttu-id="dbb3e-123">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="dbb3e-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
