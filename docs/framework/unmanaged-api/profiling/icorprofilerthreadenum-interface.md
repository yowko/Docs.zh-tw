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
ms.workload: dotnet
ms.openlocfilehash: 4758d97aab0b4827ba955922c6b14f35ff0f3f81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="9548b-102">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="9548b-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="9548b-103">提供方法，以循序逐一查看 Common Language Runtime 中的執行緒集合。</span><span class="sxs-lookup"><span data-stu-id="9548b-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9548b-104">方法</span><span class="sxs-lookup"><span data-stu-id="9548b-104">Methods</span></span>  
  
|<span data-ttu-id="9548b-105">方法</span><span class="sxs-lookup"><span data-stu-id="9548b-105">Method</span></span>|<span data-ttu-id="9548b-106">描述</span><span class="sxs-lookup"><span data-stu-id="9548b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9548b-107">Clone 方法</span><span class="sxs-lookup"><span data-stu-id="9548b-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="9548b-108">取得這個 `ICorProfilerThreadEnum` 介面複本的介面指標。</span><span class="sxs-lookup"><span data-stu-id="9548b-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="9548b-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="9548b-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="9548b-110">取得應用程式所使用的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="9548b-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="9548b-111">Next 方法</span><span class="sxs-lookup"><span data-stu-id="9548b-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="9548b-112">從循序執行緒集合中取得指定的連續執行緒數目，從序列中列舉值的目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="9548b-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="9548b-113">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="9548b-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="9548b-114">將列舉值的資料指標移至序列的開始位置。</span><span class="sxs-lookup"><span data-stu-id="9548b-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="9548b-115">Skip 方法</span><span class="sxs-lookup"><span data-stu-id="9548b-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="9548b-116">將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。</span><span class="sxs-lookup"><span data-stu-id="9548b-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9548b-117">備註</span><span class="sxs-lookup"><span data-stu-id="9548b-117">Remarks</span></span>  
 <span data-ttu-id="9548b-118">`ICorProfilerThreadEnum` 介面是列舉值。</span><span class="sxs-lookup"><span data-stu-id="9548b-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="9548b-119">它可讓陣列的接收端以適合接收端的速率，從傳送端提取項目。</span><span class="sxs-lookup"><span data-stu-id="9548b-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="9548b-120">換句話說，接收端能夠明確控制陣列項目的流程，因此可避免發生與傳遞大型陣列做為方法參數相關的問題。</span><span class="sxs-lookup"><span data-stu-id="9548b-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9548b-121">需求</span><span class="sxs-lookup"><span data-stu-id="9548b-121">Requirements</span></span>  
 <span data-ttu-id="9548b-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9548b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9548b-123">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9548b-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9548b-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9548b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9548b-125">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9548b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9548b-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="9548b-126">See Also</span></span>  
 [<span data-ttu-id="9548b-127">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="9548b-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="9548b-128">分析介面</span><span class="sxs-lookup"><span data-stu-id="9548b-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
