---
title: "ICorDebugProcess5::EnumerateHeapRegions 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHeapRegions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 478a8490e57946a08670d9f86e1f6ebcc67703a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="56759-102">ICorDebugProcess5::EnumerateHeapRegions 方法</span><span class="sxs-lookup"><span data-stu-id="56759-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="56759-103">取得 managed 堆積的記憶體範圍的列舉值。</span><span class="sxs-lookup"><span data-stu-id="56759-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56759-104">語法</span><span class="sxs-lookup"><span data-stu-id="56759-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56759-105">參數</span><span class="sxs-lookup"><span data-stu-id="56759-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="56759-106">[out]位址指標[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)介面物件的物件位於 managed 堆積中的記憶體範圍的列舉值。</span><span class="sxs-lookup"><span data-stu-id="56759-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56759-107">備註</span><span class="sxs-lookup"><span data-stu-id="56759-107">Remarks</span></span>  
 <span data-ttu-id="56759-108">然後再呼叫`ICorDebugProcess5::EnumerateHeapRegions`方法，您應該呼叫[icordebugprocess5:: Getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)方法，並檢查的值`areGCStructuresValid`欄位傳回[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)若要確保記憶體回收堆積中目前的狀態是可列舉物件。</span><span class="sxs-lookup"><span data-stu-id="56759-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="56759-109">此外，`ICorDebugProcess5::EnumerateHeapRegions`方法會傳回`E_FAIL`附加過早在程序的存留期時，如果之前的記憶體區域建立。</span><span class="sxs-lookup"><span data-stu-id="56759-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="56759-110">這個方法保證來列舉所有可能會包含受管理的物件的記憶體區域，但是它並不保證 managed 的物件實際位於這些區域。</span><span class="sxs-lookup"><span data-stu-id="56759-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="56759-111">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)集合物件可能包含空白或保留的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="56759-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="56759-112">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)介面的物件是衍生自 ICorDebugEnum 介面，可讓您列舉的標準列舉值[COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="56759-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="56759-113">每個[COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)物件提供的特定區段，以及該區段中的物件層代的記憶體範圍的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="56759-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56759-114">需求</span><span class="sxs-lookup"><span data-stu-id="56759-114">Requirements</span></span>  
 <span data-ttu-id="56759-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="56759-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56759-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56759-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56759-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56759-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56759-118">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56759-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56759-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="56759-119">See Also</span></span>  
 [<span data-ttu-id="56759-120">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="56759-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="56759-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="56759-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
