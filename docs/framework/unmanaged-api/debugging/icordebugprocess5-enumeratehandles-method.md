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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f2177702c6c5999033d0852a932e52c0725fb8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422655"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="d0299-102">ICorDebugProcess5::EnumerateHandles 方法</span><span class="sxs-lookup"><span data-stu-id="d0299-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="d0299-103">取得物件控點的程序中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d0299-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0299-104">語法</span><span class="sxs-lookup"><span data-stu-id="d0299-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0299-105">參數</span><span class="sxs-lookup"><span data-stu-id="d0299-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="d0299-106">[in]位元組合[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)值，指定要包含在集合中的控制代碼的類型。</span><span class="sxs-lookup"><span data-stu-id="d0299-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="d0299-107">[out]位址指標[ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)也就是列舉值物件以進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="d0299-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0299-108">備註</span><span class="sxs-lookup"><span data-stu-id="d0299-108">Remarks</span></span>  
 <span data-ttu-id="d0299-109">`EnumerateHandles` 是 helper 函式支援的控制代碼資料表檢查。</span><span class="sxs-lookup"><span data-stu-id="d0299-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="d0299-110">類似於[icordebugprocess5:: Enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)方法，而不是填入[ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)集合的所有物件，若要進行記憶體回收，它包含有控制代碼資料表中的控制代碼的物件。</span><span class="sxs-lookup"><span data-stu-id="d0299-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="d0299-111">`types`參數會指定要包含在集合中的控制代碼類型。</span><span class="sxs-lookup"><span data-stu-id="d0299-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="d0299-112">`types` 可以是下列三個成員[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)列舉型別：</span><span class="sxs-lookup"><span data-stu-id="d0299-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
-   <span data-ttu-id="d0299-113">`CorHandleStrongOnly` （僅限強式參考來控制代碼）。</span><span class="sxs-lookup"><span data-stu-id="d0299-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
-   <span data-ttu-id="d0299-114">`CorHandleWeakOnly` （僅限弱式參考來控制代碼）。</span><span class="sxs-lookup"><span data-stu-id="d0299-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
-   <span data-ttu-id="d0299-115">`CorHandleAll` （所有控制代碼）。</span><span class="sxs-lookup"><span data-stu-id="d0299-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0299-116">需求</span><span class="sxs-lookup"><span data-stu-id="d0299-116">Requirements</span></span>  
 <span data-ttu-id="d0299-117">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0299-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0299-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0299-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0299-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0299-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0299-120">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0299-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0299-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0299-121">See Also</span></span>  
 [<span data-ttu-id="d0299-122">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="d0299-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="d0299-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="d0299-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
