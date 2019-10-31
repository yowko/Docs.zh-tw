---
title: ICorDebugProcess5::EnumerateGCReferences 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: 84b5da043f9bd437ee9099135ba865c1ab23bb9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129662"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="0cb0a-102">ICorDebugProcess5::EnumerateGCReferences 方法</span><span class="sxs-lookup"><span data-stu-id="0cb0a-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="0cb0a-103">取得要在進程中進行垃圾收集之所有物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="0cb0a-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb0a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0cb0a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cb0a-105">參數</span><span class="sxs-lookup"><span data-stu-id="0cb0a-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="0cb0a-106">在布林值，指出是否也要列舉弱式參考。</span><span class="sxs-lookup"><span data-stu-id="0cb0a-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="0cb0a-107">如果 `true``enumerateWeakReferences`，則 `ppEnum` 列舉值同時包含強式參考和弱式參考。</span><span class="sxs-lookup"><span data-stu-id="0cb0a-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="0cb0a-108">如果 `false``enumerateWeakReferences`，列舉值只會包含強式參考。</span><span class="sxs-lookup"><span data-stu-id="0cb0a-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="0cb0a-109">脫銷[ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)位址的指標，這是要進行垃圾收集之物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="0cb0a-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cb0a-110">備註</span><span class="sxs-lookup"><span data-stu-id="0cb0a-110">Remarks</span></span>  
 <span data-ttu-id="0cb0a-111">這個方法可讓您判斷進程中任何 managed 物件的完整根鏈，並可用來判斷物件為何仍然處於作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="0cb0a-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cb0a-112">需求</span><span class="sxs-lookup"><span data-stu-id="0cb0a-112">Requirements</span></span>  
 <span data-ttu-id="0cb0a-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0cb0a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cb0a-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0cb0a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cb0a-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cb0a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cb0a-116">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cb0a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb0a-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="0cb0a-117">See also</span></span>

- [<span data-ttu-id="0cb0a-118">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="0cb0a-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="0cb0a-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0cb0a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
