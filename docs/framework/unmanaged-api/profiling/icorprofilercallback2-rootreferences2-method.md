---
title: ICorProfilerCallback2::RootReferences2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
ms.openlocfilehash: 9e53e7bcecd900bb6c71d0a822e9b63ff6726e58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729508"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="29768-102">ICorProfilerCallback2::RootReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="29768-102">ICorProfilerCallback2::RootReferences2 Method</span></span>

<span data-ttu-id="29768-103">在垃圾收集發生之後，通知分析工具有關根參考。</span><span class="sxs-lookup"><span data-stu-id="29768-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="29768-104">這個方法是 [ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md) 方法的延伸。</span><span class="sxs-lookup"><span data-stu-id="29768-104">This method is an extension of the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29768-105">語法</span><span class="sxs-lookup"><span data-stu-id="29768-105">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29768-106">參數</span><span class="sxs-lookup"><span data-stu-id="29768-106">Parameters</span></span>  

 `cRootRefs`  
 <span data-ttu-id="29768-107">在 `rootRefIds`、 `rootKinds` 、 `rootFlags` 和陣列中的元素數目 `rootIds` 。</span><span class="sxs-lookup"><span data-stu-id="29768-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="29768-108">在物件識別碼的陣列，每個物件都會參考靜態物件或堆疊上的物件。</span><span class="sxs-lookup"><span data-stu-id="29768-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="29768-109">陣列中的專案會 `rootKinds` 提供資訊，以分類陣列中的對應元素 `rootRefIds` 。</span><span class="sxs-lookup"><span data-stu-id="29768-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="29768-110">在 [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) 值的陣列，表示垃圾收集根目錄的型別。</span><span class="sxs-lookup"><span data-stu-id="29768-110">[in] An array of [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="29768-111">在 [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) 值的陣列，這些值會描述垃圾收集根目錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="29768-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="29768-112">在UINT_PTR 值的陣列，這些值會根據參數的值，指向包含垃圾收集根目錄之其他資訊的整數 `rootKinds` 。</span><span class="sxs-lookup"><span data-stu-id="29768-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="29768-113">如果根的型別是堆疊，則根識別碼適用于包含變數的函式。</span><span class="sxs-lookup"><span data-stu-id="29768-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="29768-114">如果該根識別碼為0，則函式是 CLR 內部的未命名函數。</span><span class="sxs-lookup"><span data-stu-id="29768-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="29768-115">如果根的型別是控制碼，則根識別碼是用於垃圾收集控制碼。</span><span class="sxs-lookup"><span data-stu-id="29768-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="29768-116">如果是其他根類型，則識別碼是不透明的值，應予以忽略。</span><span class="sxs-lookup"><span data-stu-id="29768-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29768-117">備註</span><span class="sxs-lookup"><span data-stu-id="29768-117">Remarks</span></span>  

 <span data-ttu-id="29768-118">`rootRefIds`、、 `rootKinds` `rootFlags` 和 `rootIds` 陣列是平行陣列。</span><span class="sxs-lookup"><span data-stu-id="29768-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="29768-119">也就是說，、 `rootRefIds[i]` 、 `rootKinds[i]` `rootFlags[i]` 和 `rootIds[i]` 全都關注相同的根。</span><span class="sxs-lookup"><span data-stu-id="29768-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="29768-120">`RootReferences`和 `RootReferences2` 都被呼叫，以通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="29768-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="29768-121">分析工具通常會實作為一種方法，但不會同時執行兩者，因為傳入的資訊 `RootReferences2` 是傳入的超集合 `RootReferences` 。</span><span class="sxs-lookup"><span data-stu-id="29768-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="29768-122">中的專案可能是 `rootRefIds` 零，這表示對應的根參考為 null，且未參考 managed 堆積上的物件。</span><span class="sxs-lookup"><span data-stu-id="29768-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="29768-123">在 `RootReferences2` 回呼本身期間，傳回的物件識別碼不是有效的，因為垃圾收集可能是在將物件從舊位址移至新位址的中間。</span><span class="sxs-lookup"><span data-stu-id="29768-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="29768-124">因此，分析工具不應嘗試在 `RootReferences2` 呼叫期間檢查物件。</span><span class="sxs-lookup"><span data-stu-id="29768-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="29768-125">呼叫 [ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) 時，所有物件都已移至其新位置，而且可以安全地進行檢查。</span><span class="sxs-lookup"><span data-stu-id="29768-125">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29768-126">需求</span><span class="sxs-lookup"><span data-stu-id="29768-126">Requirements</span></span>  

 <span data-ttu-id="29768-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29768-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29768-128">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29768-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29768-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29768-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29768-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29768-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29768-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29768-131">See also</span></span>

- [<span data-ttu-id="29768-132">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="29768-132">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="29768-133">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="29768-133">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
