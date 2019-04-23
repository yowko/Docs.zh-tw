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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0845165e3200d7a5e14715cbe116ea5255aa021
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178889"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="3016f-102">ICorDebugProcess5::EnumerateGCReferences 方法</span><span class="sxs-lookup"><span data-stu-id="3016f-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="3016f-103">取得要進行記憶體回收處理序中的所有物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="3016f-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3016f-104">語法</span><span class="sxs-lookup"><span data-stu-id="3016f-104">Syntax</span></span>  
  
```  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3016f-105">參數</span><span class="sxs-lookup"><span data-stu-id="3016f-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="3016f-106">[in]布林值，指出弱式參考是否也要列舉。</span><span class="sxs-lookup"><span data-stu-id="3016f-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="3016f-107">如果`enumerateWeakReferences`已`true`，則`ppEnum`強式參考和弱式參考，包含列舉值。</span><span class="sxs-lookup"><span data-stu-id="3016f-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="3016f-108">如果`enumerateWeakReferences`是`false`，此列舉值會包含只有強式參考。</span><span class="sxs-lookup"><span data-stu-id="3016f-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="3016f-109">[out]位址指標[ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)也就是列舉值的物件進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="3016f-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3016f-110">備註</span><span class="sxs-lookup"><span data-stu-id="3016f-110">Remarks</span></span>  
 <span data-ttu-id="3016f-111">這個方法會提供一個方式來判斷處理程序中的任何 managed 物件的完整根鏈結，而且可用來判斷為何仍在執行物件。</span><span class="sxs-lookup"><span data-stu-id="3016f-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3016f-112">需求</span><span class="sxs-lookup"><span data-stu-id="3016f-112">Requirements</span></span>  
 <span data-ttu-id="3016f-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3016f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3016f-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3016f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3016f-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3016f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3016f-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3016f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3016f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3016f-117">See also</span></span>

- [<span data-ttu-id="3016f-118">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="3016f-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="3016f-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3016f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
