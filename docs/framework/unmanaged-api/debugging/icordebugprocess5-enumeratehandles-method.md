---
title: ICorDebugProcess5::EnumerateHandles 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
ms.openlocfilehash: e0e68dba1f4d9ac5fa618aa842b823dcc046e70e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129684"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="f2d39-102">ICorDebugProcess5::EnumerateHandles 方法</span><span class="sxs-lookup"><span data-stu-id="f2d39-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="f2d39-103">取得進程中物件控制碼的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f2d39-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2d39-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2d39-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2d39-105">參數</span><span class="sxs-lookup"><span data-stu-id="f2d39-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="f2d39-106">在[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)值的位元組合，這個組合會指定要包含在集合中的控制碼類型。</span><span class="sxs-lookup"><span data-stu-id="f2d39-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="f2d39-107">脫銷[ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)位址的指標，這是要進行垃圾收集之物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f2d39-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2d39-108">備註</span><span class="sxs-lookup"><span data-stu-id="f2d39-108">Remarks</span></span>  
 <span data-ttu-id="f2d39-109">`EnumerateHandles` 是支援檢查控制碼資料表的 helper 函數。</span><span class="sxs-lookup"><span data-stu-id="f2d39-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="f2d39-110">它類似于[ICorDebugProcess5：： EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)方法，不同之處在于它不會填入包含所有要進行垃圾收集之物件的[ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)集合，只會包含具有來自的控制碼的物件。控制碼資料表。</span><span class="sxs-lookup"><span data-stu-id="f2d39-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="f2d39-111">`types` 參數會指定要包含在集合中的控制碼類型。</span><span class="sxs-lookup"><span data-stu-id="f2d39-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="f2d39-112">`types` 可以是[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)列舉的下列三個成員中的任何一個：</span><span class="sxs-lookup"><span data-stu-id="f2d39-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="f2d39-113">`CorHandleStrongOnly` （僅限強式參考的控制碼）。</span><span class="sxs-lookup"><span data-stu-id="f2d39-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="f2d39-114">`CorHandleWeakOnly` （僅限弱式參考的控制碼）。</span><span class="sxs-lookup"><span data-stu-id="f2d39-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="f2d39-115">`CorHandleAll` （所有控制碼）。</span><span class="sxs-lookup"><span data-stu-id="f2d39-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2d39-116">需求</span><span class="sxs-lookup"><span data-stu-id="f2d39-116">Requirements</span></span>  
 <span data-ttu-id="f2d39-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2d39-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2d39-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2d39-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2d39-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2d39-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2d39-120">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2d39-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2d39-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="f2d39-121">See also</span></span>

- [<span data-ttu-id="f2d39-122">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="f2d39-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="f2d39-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="f2d39-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
