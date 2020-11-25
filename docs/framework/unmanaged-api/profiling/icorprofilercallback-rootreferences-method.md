---
title: ICorProfilerCallback::RootReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
ms.openlocfilehash: 2d084ce0a785ba37c5b7dc937ed116cee74b7594
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720655"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="b22d8-102">ICorProfilerCallback::RootReferences 方法</span><span class="sxs-lookup"><span data-stu-id="b22d8-102">ICorProfilerCallback::RootReferences Method</span></span>

<span data-ttu-id="b22d8-103">在垃圾收集之後，以根參考的相關語音總機 profiler。</span><span class="sxs-lookup"><span data-stu-id="b22d8-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b22d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="b22d8-104">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b22d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="b22d8-105">Parameters</span></span>  

 `cRootRefs`  
 <span data-ttu-id="b22d8-106">在陣列中的參考數目 `rootRefIds` 。</span><span class="sxs-lookup"><span data-stu-id="b22d8-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="b22d8-107">在物件識別碼的陣列，參考靜態物件或堆疊上的物件。</span><span class="sxs-lookup"><span data-stu-id="b22d8-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b22d8-108">備註</span><span class="sxs-lookup"><span data-stu-id="b22d8-108">Remarks</span></span>  

 <span data-ttu-id="b22d8-109">`RootReferences`和[ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md)都會呼叫以通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="b22d8-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="b22d8-110">分析工具通常會執行其中一項，但不能同時執行，因為傳入的資訊 `RootReferences2` 是傳入的超集合 `RootReferences` 。</span><span class="sxs-lookup"><span data-stu-id="b22d8-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="b22d8-111">`rootRefIds`陣列可能包含 null 物件。</span><span class="sxs-lookup"><span data-stu-id="b22d8-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="b22d8-112">例如，在堆疊上宣告的所有物件參考都會被垃圾收集行程視為根，而且一律會進行報告。</span><span class="sxs-lookup"><span data-stu-id="b22d8-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="b22d8-113">在 `RootReferences` 回呼本身期間，傳回的物件識別碼不是有效的，因為垃圾收集可能是在將物件從舊位址移至新位址的中間。</span><span class="sxs-lookup"><span data-stu-id="b22d8-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="b22d8-114">因此，分析工具不能在呼叫期間嘗試檢查物件 `RootReferences` 。</span><span class="sxs-lookup"><span data-stu-id="b22d8-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="b22d8-115">呼叫 [ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) 時，所有物件都已移至其新位置，而且可以安全地進行檢查。</span><span class="sxs-lookup"><span data-stu-id="b22d8-115">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b22d8-116">需求</span><span class="sxs-lookup"><span data-stu-id="b22d8-116">Requirements</span></span>  

 <span data-ttu-id="b22d8-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b22d8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b22d8-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b22d8-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b22d8-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b22d8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b22d8-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b22d8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b22d8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b22d8-121">See also</span></span>

- [<span data-ttu-id="b22d8-122">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b22d8-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
