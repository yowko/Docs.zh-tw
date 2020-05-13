---
title: ICorDebugHeapSegmentEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: 0a5a87c71bea603073c35dd851e443ca8c497523
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210432"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="37121-102">ICorDebugHeapSegmentEnum 介面</span><span class="sxs-lookup"><span data-stu-id="37121-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="37121-103">為 Managed 堆積的記憶體區域提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="37121-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="37121-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="37121-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37121-105">方法</span><span class="sxs-lookup"><span data-stu-id="37121-105">Methods</span></span>  
  
|<span data-ttu-id="37121-106">方法</span><span class="sxs-lookup"><span data-stu-id="37121-106">Method</span></span>|<span data-ttu-id="37121-107">描述</span><span class="sxs-lookup"><span data-stu-id="37121-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37121-108">下一個方法</span><span class="sxs-lookup"><span data-stu-id="37121-108">Next Method</span></span>](icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="37121-109">取得指定的[COR_HEAPOBJECT](cor-heapobject-structure.md)實例數目，其中包含 managed 堆積區域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="37121-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37121-110">備註</span><span class="sxs-lookup"><span data-stu-id="37121-110">Remarks</span></span>  
 <span data-ttu-id="37121-111">介面會實 `ICorDebugHeapSegmentEnum` ICorDebugEnum 介面。</span><span class="sxs-lookup"><span data-stu-id="37121-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="37121-112">`ICorDebugHeapSegmentEnum`實例會藉由呼叫[ICorDebugProcess5：： EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md)方法來填入[COR_HEAPOBJECT](cor-heapobject-structure.md)實例。</span><span class="sxs-lookup"><span data-stu-id="37121-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="37121-113">您可以藉由呼叫[ICorDebugHeapSegmentEnum：： Next](icordebugheapsegmentenum-next-method.md)方法來列舉集合中的[COR_HEAPOBJECT](cor-heapobject-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="37121-113">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="37121-114">`ICorDebugHeapSegmentEnum`集合物件會列舉可能包含 managed 物件的所有記憶體區域，但不保證 managed 物件實際上位於這些區域中。</span><span class="sxs-lookup"><span data-stu-id="37121-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="37121-115">其中可能包含空的或保留的記憶體區域相關資訊。</span><span class="sxs-lookup"><span data-stu-id="37121-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37121-116">需求</span><span class="sxs-lookup"><span data-stu-id="37121-116">Requirements</span></span>  
 <span data-ttu-id="37121-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37121-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37121-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37121-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37121-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37121-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37121-120">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37121-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37121-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="37121-121">See also</span></span>

- [<span data-ttu-id="37121-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="37121-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
