---
title: ICorProfilerInfo10 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4c5d553744008734037975d6e63e1b07b89cf886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175066"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="fb648-102">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="fb648-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="fb648-103">[ICorProfilerInfo9](icorprofilerinfo9-interface.md)的子類，它提供修改函數 IL、查詢運行時資訊以及掛起和恢復運行時的方法。</span><span class="sxs-lookup"><span data-stu-id="fb648-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="fb648-104">方法</span><span class="sxs-lookup"><span data-stu-id="fb648-104">Methods</span></span>  

| <span data-ttu-id="fb648-105">方法</span><span class="sxs-lookup"><span data-stu-id="fb648-105">Method</span></span>|<span data-ttu-id="fb648-106">描述</span><span class="sxs-lookup"><span data-stu-id="fb648-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="fb648-107">EnumerateObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="fb648-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="fb648-108">給定 ObjectID、回檔和用戶端資料，枚舉每個物件引用（如果有）。</span><span class="sxs-lookup"><span data-stu-id="fb648-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="fb648-109">IsFrozenObject 方法</span><span class="sxs-lookup"><span data-stu-id="fb648-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="fb648-110">給定 ObjectID，確定物件是否位於唯讀段中。</span><span class="sxs-lookup"><span data-stu-id="fb648-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="fb648-111">GetLOHObjectSizeThreshold 方法</span><span class="sxs-lookup"><span data-stu-id="fb648-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="fb648-112">獲取配置的 LOH 閾值。</span><span class="sxs-lookup"><span data-stu-id="fb648-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="fb648-113">RequestReJITWithInliners 方法</span><span class="sxs-lookup"><span data-stu-id="fb648-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="fb648-114">重新執行請求的方法，以及所請求方法的任何內襯。</span><span class="sxs-lookup"><span data-stu-id="fb648-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="fb648-115">SuspendRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="fb648-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="fb648-116">在不執行 GC 的情況下掛起運行時。</span><span class="sxs-lookup"><span data-stu-id="fb648-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="fb648-117">ResumeRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="fb648-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="fb648-118">在不執行 GC 的情況下恢復運行時。</span><span class="sxs-lookup"><span data-stu-id="fb648-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="fb648-119">需求</span><span class="sxs-lookup"><span data-stu-id="fb648-119">Requirements</span></span>  
<span data-ttu-id="fb648-120">**平臺：** 請參閱[.NET Core 支援的作業系統](../../../core/install/dependencies.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="fb648-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
<span data-ttu-id="fb648-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb648-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="fb648-122">**.NET 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb648-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fb648-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb648-123">See also</span></span>

- [<span data-ttu-id="fb648-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="fb648-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
