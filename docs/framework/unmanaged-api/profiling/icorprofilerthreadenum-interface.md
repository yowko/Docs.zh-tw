---
title: "ICorProfilerThreadEnum 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum
helpviewer_keywords: ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2ce48c836070018059becd1ece269ce7c878c7ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="c62c2-102">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="c62c2-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="c62c2-103">提供方法，以循序逐一查看 Common Language Runtime 中的執行緒集合。</span><span class="sxs-lookup"><span data-stu-id="c62c2-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c62c2-104">方法</span><span class="sxs-lookup"><span data-stu-id="c62c2-104">Methods</span></span>  
  
|<span data-ttu-id="c62c2-105">方法</span><span class="sxs-lookup"><span data-stu-id="c62c2-105">Method</span></span>|<span data-ttu-id="c62c2-106">說明</span><span class="sxs-lookup"><span data-stu-id="c62c2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c62c2-107">Clone 方法</span><span class="sxs-lookup"><span data-stu-id="c62c2-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="c62c2-108">取得這個 `ICorProfilerThreadEnum` 介面複本的介面指標。</span><span class="sxs-lookup"><span data-stu-id="c62c2-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="c62c2-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="c62c2-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="c62c2-110">取得應用程式所使用的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="c62c2-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="c62c2-111">Next 方法</span><span class="sxs-lookup"><span data-stu-id="c62c2-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="c62c2-112">從循序執行緒集合中取得指定的連續執行緒數目，從序列中列舉值的目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="c62c2-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="c62c2-113">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="c62c2-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="c62c2-114">將列舉值的資料指標移至序列的開始位置。</span><span class="sxs-lookup"><span data-stu-id="c62c2-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="c62c2-115">Skip 方法</span><span class="sxs-lookup"><span data-stu-id="c62c2-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="c62c2-116">將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。</span><span class="sxs-lookup"><span data-stu-id="c62c2-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c62c2-117">備註</span><span class="sxs-lookup"><span data-stu-id="c62c2-117">Remarks</span></span>  
 <span data-ttu-id="c62c2-118">`ICorProfilerThreadEnum` 介面是列舉值。</span><span class="sxs-lookup"><span data-stu-id="c62c2-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="c62c2-119">它可讓陣列的接收端以適合接收端的速率，從傳送端提取項目。</span><span class="sxs-lookup"><span data-stu-id="c62c2-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="c62c2-120">換句話說，接收端能夠明確控制陣列項目的流程，因此可避免發生與傳遞大型陣列做為方法參數相關的問題。</span><span class="sxs-lookup"><span data-stu-id="c62c2-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c62c2-121">需求</span><span class="sxs-lookup"><span data-stu-id="c62c2-121">Requirements</span></span>  
 <span data-ttu-id="c62c2-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c62c2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c62c2-123">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c62c2-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c62c2-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c62c2-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c62c2-125">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c62c2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c62c2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c62c2-126">See Also</span></span>  
 [<span data-ttu-id="c62c2-127">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="c62c2-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="c62c2-128">分析介面</span><span class="sxs-lookup"><span data-stu-id="c62c2-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
