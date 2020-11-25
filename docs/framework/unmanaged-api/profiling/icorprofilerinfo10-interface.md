---
title: ICorProfilerInfo10 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: a99fa8410bbd0dedeaeb9e1713107a3dcc9ada6b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727220"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="964ab-102">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="964ab-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="964ab-103">[ICorProfilerInfo9](icorprofilerinfo9-interface.md)的子類別，可提供修改函式 IL 的方法、從執行時間查詢資訊，以及暫停和繼續執行時間。</span><span class="sxs-lookup"><span data-stu-id="964ab-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="964ab-104">方法</span><span class="sxs-lookup"><span data-stu-id="964ab-104">Methods</span></span>  

| <span data-ttu-id="964ab-105">方法</span><span class="sxs-lookup"><span data-stu-id="964ab-105">Method</span></span>|<span data-ttu-id="964ab-106">描述</span><span class="sxs-lookup"><span data-stu-id="964ab-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="964ab-107">EnumerateObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="964ab-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="964ab-108">如果有 ObjectID，回呼和 clientData 會列舉每個物件參考 (是否有任何) 。</span><span class="sxs-lookup"><span data-stu-id="964ab-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="964ab-109">IsFrozenObject 方法</span><span class="sxs-lookup"><span data-stu-id="964ab-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="964ab-110">指定 ObjectID 之後，判斷物件是否在唯讀區段中。</span><span class="sxs-lookup"><span data-stu-id="964ab-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="964ab-111">GetLOHObjectSizeThreshold 方法</span><span class="sxs-lookup"><span data-stu-id="964ab-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="964ab-112">取得已設定之 LOH 臨界值的值。</span><span class="sxs-lookup"><span data-stu-id="964ab-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="964ab-113">RequestReJITWithInliners 方法</span><span class="sxs-lookup"><span data-stu-id="964ab-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="964ab-114">ReJITs 所要求的方法，以及所要求之方法的任何 inliners。</span><span class="sxs-lookup"><span data-stu-id="964ab-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="964ab-115">SuspendRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="964ab-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="964ab-116">暫停執行時間，而不執行 GC。</span><span class="sxs-lookup"><span data-stu-id="964ab-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="964ab-117">ResumeRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="964ab-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="964ab-118">繼續執行時間，而不執行 GC。</span><span class="sxs-lookup"><span data-stu-id="964ab-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="964ab-119">需求</span><span class="sxs-lookup"><span data-stu-id="964ab-119">Requirements</span></span>  

<span data-ttu-id="964ab-120">**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="964ab-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="964ab-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="964ab-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="964ab-122">**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="964ab-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="964ab-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="964ab-123">See also</span></span>

- [<span data-ttu-id="964ab-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="964ab-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
