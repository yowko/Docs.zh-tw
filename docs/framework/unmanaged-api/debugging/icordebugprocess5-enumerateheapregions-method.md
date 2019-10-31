---
title: ICorDebugProcess5::EnumerateHeapRegions 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
ms.openlocfilehash: 3ab4da3fcf43731587dae6f3a8e82ea48c5ee1ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129635"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="9f884-102">ICorDebugProcess5::EnumerateHeapRegions 方法</span><span class="sxs-lookup"><span data-stu-id="9f884-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="9f884-103">取得 managed 堆積記憶體範圍的列舉值。</span><span class="sxs-lookup"><span data-stu-id="9f884-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f884-104">語法</span><span class="sxs-lookup"><span data-stu-id="9f884-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f884-105">參數</span><span class="sxs-lookup"><span data-stu-id="9f884-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="9f884-106">脫銷[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)介面物件之位址的指標，這是物件位於 managed 堆積中的記憶體範圍的列舉值。</span><span class="sxs-lookup"><span data-stu-id="9f884-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f884-107">備註</span><span class="sxs-lookup"><span data-stu-id="9f884-107">Remarks</span></span>  
 <span data-ttu-id="9f884-108">在呼叫 `ICorDebugProcess5::EnumerateHeapRegions` 方法之前，您應該呼叫[ICorDebugProcess5：： GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)方法，並檢查所傳回之[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)物件的 `areGCStructuresValid` 欄位值，以確保其中的垃圾收集堆積目前的狀態是可列舉的。</span><span class="sxs-lookup"><span data-stu-id="9f884-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="9f884-109">此外，如果您在進程的存留期間過早附加記憶體區域，則 `ICorDebugProcess5::EnumerateHeapRegions` 方法會傳回 `E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="9f884-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="9f884-110">這個方法一定會列舉可能包含 managed 物件的所有記憶體區域，但不保證 managed 物件實際上位於這些區域中。</span><span class="sxs-lookup"><span data-stu-id="9f884-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="9f884-111">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)集合物件可能包含空的或保留的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="9f884-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="9f884-112">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)介面物件是衍生自 ICorDebugEnum 介面的標準列舉值，可讓您列舉[COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="9f884-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="9f884-113">每個[COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)物件都會提供特定區段之記憶體範圍的相關資訊，以及該區段中的物件產生。</span><span class="sxs-lookup"><span data-stu-id="9f884-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f884-114">需求</span><span class="sxs-lookup"><span data-stu-id="9f884-114">Requirements</span></span>  
 <span data-ttu-id="9f884-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9f884-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f884-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f884-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f884-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f884-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f884-118">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f884-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f884-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="9f884-119">See also</span></span>

- [<span data-ttu-id="9f884-120">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="9f884-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="9f884-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9f884-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
