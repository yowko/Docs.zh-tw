---
title: ICorDebugProcess5::EnumerateHeap 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: 780f9eb0984e35c4487d770b5e7ff33917cf07ed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792420"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="ceee1-102">ICorDebugProcess5::EnumerateHeap 方法</span><span class="sxs-lookup"><span data-stu-id="ceee1-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="ceee1-103">取得 managed 堆積上物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="ceee1-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceee1-104">語法</span><span class="sxs-lookup"><span data-stu-id="ceee1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ceee1-105">參數</span><span class="sxs-lookup"><span data-stu-id="ceee1-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="ceee1-106">脫銷[ICorDebugHeapEnum](icordebugheapenum-interface.md)介面物件之位址的指標，這是位於 managed 堆積上之物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="ceee1-106">[out] A pointer to the address of an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ceee1-107">備註</span><span class="sxs-lookup"><span data-stu-id="ceee1-107">Remarks</span></span>  
 <span data-ttu-id="ceee1-108">在呼叫 `ICorDebugProcess5::EnumerateHeap` 方法之前，您應該呼叫[ICorDebugProcess5：： GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md)方法，並檢查所傳回[COR_HEAPINFO](cor-heapinfo-structure.md)物件的 `areGCStructuresValid` 欄位值，以確保其目前狀態中的垃圾收集堆積是可列舉的。</span><span class="sxs-lookup"><span data-stu-id="ceee1-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="ceee1-109">此外，如果您在進程的存留期間內過早附加，則 `ICorDebugProcess5::EnumerateHeap` 會傳回 `E_FAIL`，然後才會配置受控堆積的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ceee1-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="ceee1-110">[ICorDebugHeapEnum](icordebugheapenum-interface.md)介面物件是衍生自 ICorDebugEnum 介面的標準列舉值，可讓您列舉[COR_HEAPOBJECT](cor-heapobject-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="ceee1-110">The [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="ceee1-111">這個方法會在[ICorDebugHeapEnum](icordebugheapenum-interface.md)集合物件中填入提供所有物件相關資訊的[COR_HEAPOBJECT](cor-heapobject-structure.md)實例。</span><span class="sxs-lookup"><span data-stu-id="ceee1-111">This method populates the [ICorDebugHeapEnum](icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="ceee1-112">此集合也可以包含[COR_HEAPOBJECT](cor-heapobject-structure.md)實例，這些實例會提供未由任何物件（但垃圾收集行程尚未收集）之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ceee1-112">The collection may also include [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceee1-113">需求</span><span class="sxs-lookup"><span data-stu-id="ceee1-113">Requirements</span></span>  
 <span data-ttu-id="ceee1-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ceee1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceee1-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ceee1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ceee1-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ceee1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ceee1-117">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceee1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceee1-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="ceee1-118">See also</span></span>

- [<span data-ttu-id="ceee1-119">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="ceee1-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="ceee1-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ceee1-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
