---
title: ICorProfilerInfo10 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: e90a1ffbc037636e4296bbd4f4c3c5082885e9f3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863240"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="a0e60-102">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="a0e60-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="a0e60-103">[ICorProfilerInfo9](icorprofilerinfo9-interface.md)的子類別，提供修改函式 IL 的方法、從執行時間查詢資訊，以及暫停和繼續執行時間。</span><span class="sxs-lookup"><span data-stu-id="a0e60-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="a0e60-104">方法</span><span class="sxs-lookup"><span data-stu-id="a0e60-104">Methods</span></span>  

| <span data-ttu-id="a0e60-105">方法</span><span class="sxs-lookup"><span data-stu-id="a0e60-105">Method</span></span>|<span data-ttu-id="a0e60-106">描述</span><span class="sxs-lookup"><span data-stu-id="a0e60-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="a0e60-107">EnumerateObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="a0e60-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="a0e60-108">假設有 ObjectID、callback 和 clientData，會列舉每個物件參考（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="a0e60-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="a0e60-109">IsFrozenObject 方法</span><span class="sxs-lookup"><span data-stu-id="a0e60-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="a0e60-110">給定 ObjectID，判斷物件是否在唯讀區段中。</span><span class="sxs-lookup"><span data-stu-id="a0e60-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="a0e60-111">GetLOHObjectSizeThreshold 方法</span><span class="sxs-lookup"><span data-stu-id="a0e60-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="a0e60-112">取得設定的 LOH 臨界值。</span><span class="sxs-lookup"><span data-stu-id="a0e60-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="a0e60-113">RequestReJITWithInliners 方法</span><span class="sxs-lookup"><span data-stu-id="a0e60-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="a0e60-114">ReJITs 要求的方法，以及所要求之方法的任何 inliners。</span><span class="sxs-lookup"><span data-stu-id="a0e60-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="a0e60-115">SuspendRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="a0e60-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="a0e60-116">暫停執行時間，而不執行 GC。</span><span class="sxs-lookup"><span data-stu-id="a0e60-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="a0e60-117">ResumeRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="a0e60-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="a0e60-118">繼續執行時間，而不執行 GC。</span><span class="sxs-lookup"><span data-stu-id="a0e60-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="a0e60-119">需求</span><span class="sxs-lookup"><span data-stu-id="a0e60-119">Requirements</span></span>  
<span data-ttu-id="a0e60-120">**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="a0e60-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="a0e60-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0e60-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="a0e60-122">**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0e60-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 

## <a name="see-also"></a><span data-ttu-id="a0e60-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="a0e60-123">See also</span></span>

- [<span data-ttu-id="a0e60-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="a0e60-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
