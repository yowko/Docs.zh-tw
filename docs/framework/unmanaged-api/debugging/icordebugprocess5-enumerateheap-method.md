---
title: "ICorDebugProcess5::EnumerateHeap 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHeap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fabe3d70b493427f3845b5752946b00097c1e78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="4e79b-102">ICorDebugProcess5::EnumerateHeap 方法</span><span class="sxs-lookup"><span data-stu-id="4e79b-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="4e79b-103">取得 managed 堆積上物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="4e79b-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e79b-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e79b-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e79b-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e79b-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="4e79b-106">[out]位址指標[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)介面物件位於 managed 堆積物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="4e79b-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e79b-107">備註</span><span class="sxs-lookup"><span data-stu-id="4e79b-107">Remarks</span></span>  
 <span data-ttu-id="4e79b-108">然後再呼叫`ICorDebugProcess5::EnumerateHeap`方法，您應該呼叫[icordebugprocess5:: Getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)方法，並檢查的值`areGCStructuresValid`欄位傳回[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)若要確保記憶體回收堆積中目前的狀態是可列舉物件。</span><span class="sxs-lookup"><span data-stu-id="4e79b-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="4e79b-109">此外，`ICorDebugProcess5::EnumerateHeap`傳回`E_FAIL`如果您附加過早在程序之前記憶體的存留期的 managed 的堆積配置。</span><span class="sxs-lookup"><span data-stu-id="4e79b-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="4e79b-110">[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)介面的物件是衍生自 ICorDebugEnum 介面，可讓您列舉的標準列舉值[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="4e79b-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="4e79b-111">這個方法會填入[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)集合物件與[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)提供所有物件的相關資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4e79b-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="4e79b-112">集合也可能包括[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)提供不由任何根目錄的物件相關資訊的執行個體物件，但尚未收集記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="4e79b-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e79b-113">需求</span><span class="sxs-lookup"><span data-stu-id="4e79b-113">Requirements</span></span>  
 <span data-ttu-id="4e79b-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e79b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e79b-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e79b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e79b-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e79b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e79b-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e79b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e79b-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e79b-118">See Also</span></span>  
 [<span data-ttu-id="4e79b-119">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="4e79b-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="4e79b-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4e79b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
