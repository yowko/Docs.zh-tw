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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b616017745d7cc33d57b1626b6c27c59a0a60a32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992286"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="4fe56-102">ICorProfilerCallback::RootReferences 方法</span><span class="sxs-lookup"><span data-stu-id="4fe56-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="4fe56-103">通知分析工具，但記憶體回收之後根參考的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4fe56-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe56-104">語法</span><span class="sxs-lookup"><span data-stu-id="4fe56-104">Syntax</span></span>  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fe56-105">參數</span><span class="sxs-lookup"><span data-stu-id="4fe56-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="4fe56-106">[in]中的參考數目`rootRefIds`陣列。</span><span class="sxs-lookup"><span data-stu-id="4fe56-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="4fe56-107">[in]參考靜態物件或物件在堆疊上的物件識別碼的陣列。</span><span class="sxs-lookup"><span data-stu-id="4fe56-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fe56-108">備註</span><span class="sxs-lookup"><span data-stu-id="4fe56-108">Remarks</span></span>  
 <span data-ttu-id="4fe56-109">兩者`RootReferences`並[ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)呼叫以通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="4fe56-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="4fe56-110">分析工具通常會實作，其中一種，但非兩者皆是，因為傳入的資訊`RootReferences2`傳入的超集`RootReferences`。</span><span class="sxs-lookup"><span data-stu-id="4fe56-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="4fe56-111">可能會`rootRefIds`包含 null 物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="4fe56-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="4fe56-112">比方說，在堆疊上宣告的所有物件參考會被視為由記憶體回收行程的根目錄，並將報告。</span><span class="sxs-lookup"><span data-stu-id="4fe56-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="4fe56-113">所傳回的物件識別碼`RootReferences`不本身的回呼期間有效，因為記憶體回收可能正在將物件從舊位址移到新的位址。</span><span class="sxs-lookup"><span data-stu-id="4fe56-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="4fe56-114">因此，程式碼剖析工具不得嘗試期間檢查物件`RootReferences`呼叫。</span><span class="sxs-lookup"><span data-stu-id="4fe56-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="4fe56-115">當[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)是呼叫，所有物件都已移至其新位置和可以安全地進行檢查。</span><span class="sxs-lookup"><span data-stu-id="4fe56-115">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fe56-116">需求</span><span class="sxs-lookup"><span data-stu-id="4fe56-116">Requirements</span></span>  
 <span data-ttu-id="4fe56-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4fe56-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fe56-118">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4fe56-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4fe56-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fe56-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fe56-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fe56-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe56-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fe56-121">See also</span></span>

- [<span data-ttu-id="4fe56-122">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4fe56-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
