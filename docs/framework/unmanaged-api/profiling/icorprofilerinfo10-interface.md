---
title: ICorProfilerInfo10 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 496959ecac5b16f1faa138aec90c5194d15cb105
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974008"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="1e81c-102">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="1e81c-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="1e81c-103">[ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)的子類別, 提供修改函式 IL 的方法、從執行時間查詢資訊, 以及暫停和繼續執行時間。</span><span class="sxs-lookup"><span data-stu-id="1e81c-103">A subclass of [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="1e81c-104">方法</span><span class="sxs-lookup"><span data-stu-id="1e81c-104">Methods</span></span>  

| <span data-ttu-id="1e81c-105">方法</span><span class="sxs-lookup"><span data-stu-id="1e81c-105">Method</span></span>|<span data-ttu-id="1e81c-106">描述</span><span class="sxs-lookup"><span data-stu-id="1e81c-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="1e81c-107">EnumerateObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="1e81c-107">EnumerateObjectReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="1e81c-108">假設有 ObjectID、callback 和 clientData, 會列舉每個物件參考 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="1e81c-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="1e81c-109">IsFrozenObject 方法</span><span class="sxs-lookup"><span data-stu-id="1e81c-109">IsFrozenObject Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="1e81c-110">給定 ObjectID, 判斷物件是否在唯讀區段中。</span><span class="sxs-lookup"><span data-stu-id="1e81c-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="1e81c-111">GetLOHObjectSizeThreshold 方法</span><span class="sxs-lookup"><span data-stu-id="1e81c-111">GetLOHObjectSizeThreshold Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="1e81c-112">取得設定的 LOH 臨界值。</span><span class="sxs-lookup"><span data-stu-id="1e81c-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="1e81c-113">RequestReJITWithInliners 方法</span><span class="sxs-lookup"><span data-stu-id="1e81c-113">RequestReJITWithInliners Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="1e81c-114">ReJITs 要求的方法, 以及所要求之方法的任何 inliners。</span><span class="sxs-lookup"><span data-stu-id="1e81c-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="1e81c-115">SuspendRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="1e81c-115">SuspendRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="1e81c-116">暫停執行時間, 而不執行 GC。</span><span class="sxs-lookup"><span data-stu-id="1e81c-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="1e81c-117">ResumeRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="1e81c-117">ResumeRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="1e81c-118">繼續執行時間, 而不執行 GC。</span><span class="sxs-lookup"><span data-stu-id="1e81c-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="1e81c-119">需求</span><span class="sxs-lookup"><span data-stu-id="1e81c-119">Requirements</span></span>  
<span data-ttu-id="1e81c-120">**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="1e81c-120">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
<span data-ttu-id="1e81c-121">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="1e81c-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="1e81c-122">**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e81c-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 
## <a name="see-also"></a><span data-ttu-id="1e81c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e81c-123">See also</span></span>
- [<span data-ttu-id="1e81c-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="1e81c-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
