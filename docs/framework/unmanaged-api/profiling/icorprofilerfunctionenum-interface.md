---
title: ICorProfilerFunctionEnum 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1e55c7e6deff3928e69861541aa1a924dac263f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455058"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="e350f-102">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e350f-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="e350f-103">提供方法以循序逐一查看 Common Language Runtime 中的函式集合。</span><span class="sxs-lookup"><span data-stu-id="e350f-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e350f-104">方法</span><span class="sxs-lookup"><span data-stu-id="e350f-104">Methods</span></span>  
  
|<span data-ttu-id="e350f-105">方法</span><span class="sxs-lookup"><span data-stu-id="e350f-105">Method</span></span>|<span data-ttu-id="e350f-106">描述</span><span class="sxs-lookup"><span data-stu-id="e350f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e350f-107">Clone 方法</span><span class="sxs-lookup"><span data-stu-id="e350f-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="e350f-108">取得這個 `ICorProfilerFunctionEnum` 介面複本的介面指標。</span><span class="sxs-lookup"><span data-stu-id="e350f-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="e350f-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="e350f-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="e350f-110">取得應用程式已載入的或分析工具強制載入的函式數目。</span><span class="sxs-lookup"><span data-stu-id="e350f-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="e350f-111">Next 方法</span><span class="sxs-lookup"><span data-stu-id="e350f-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="e350f-112">於循序函式集合中，從序列中列舉值的目前位置開始，取得指定連續函式數目。</span><span class="sxs-lookup"><span data-stu-id="e350f-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="e350f-113">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="e350f-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="e350f-114">將列舉值的資料指標移至序列的開始位置。</span><span class="sxs-lookup"><span data-stu-id="e350f-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="e350f-115">Skip 方法</span><span class="sxs-lookup"><span data-stu-id="e350f-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="e350f-116">將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。</span><span class="sxs-lookup"><span data-stu-id="e350f-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e350f-117">備註</span><span class="sxs-lookup"><span data-stu-id="e350f-117">Remarks</span></span>  
 <span data-ttu-id="e350f-118">`ICorProfilerFunctionEnum` 介面是列舉值。</span><span class="sxs-lookup"><span data-stu-id="e350f-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="e350f-119">它可讓陣列的接收端以適合接收端的速率，從傳送端提取項目。</span><span class="sxs-lookup"><span data-stu-id="e350f-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="e350f-120">換句話說，接收端能夠明確控制陣列項目的流程，因此可避免與傳遞大型陣列做為方法參數相關的問題發生。</span><span class="sxs-lookup"><span data-stu-id="e350f-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="e350f-121">`ICorProfilerFunctionEnum` 列舉早已 JIT 編譯的函式，但此函式不包含從 Ngen.exe 產生的原生影像載入之函式。</span><span class="sxs-lookup"><span data-stu-id="e350f-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e350f-122">需求</span><span class="sxs-lookup"><span data-stu-id="e350f-122">Requirements</span></span>  
 <span data-ttu-id="e350f-123">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e350f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e350f-124">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e350f-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e350f-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e350f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e350f-126">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e350f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e350f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e350f-127">See Also</span></span>  
 [<span data-ttu-id="e350f-128">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e350f-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="e350f-129">分析介面</span><span class="sxs-lookup"><span data-stu-id="e350f-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="e350f-130">EnumJITedFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="e350f-130">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
