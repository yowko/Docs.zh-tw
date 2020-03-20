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
ms.openlocfilehash: a97c14d83f99c847bb8569a33e175ab6eb5bccd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178613"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="968e1-102">ICorDebugProcess5::EnumerateGCReferences 方法</span><span class="sxs-lookup"><span data-stu-id="968e1-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="968e1-103">獲取進程中要垃圾回收的所有物件的枚舉器。</span><span class="sxs-lookup"><span data-stu-id="968e1-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="968e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="968e1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="968e1-105">參數</span><span class="sxs-lookup"><span data-stu-id="968e1-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="968e1-106">[在]指示是否也枚舉弱引用的布林值。</span><span class="sxs-lookup"><span data-stu-id="968e1-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="968e1-107">如果是`enumerateWeakReferences``true`，`ppEnum`則枚舉器同時包含強引用和弱引用。</span><span class="sxs-lookup"><span data-stu-id="968e1-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="968e1-108">如果`enumerateWeakReferences``false`為 ，則枚舉器僅包含強引用。</span><span class="sxs-lookup"><span data-stu-id="968e1-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="968e1-109">[出]指向[ICorDebugGC 參考Enum](icordebuggcreferenceenum-interface.md)位址的指標，該位址是要垃圾回收的物件的枚舉器。</span><span class="sxs-lookup"><span data-stu-id="968e1-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="968e1-110">備註</span><span class="sxs-lookup"><span data-stu-id="968e1-110">Remarks</span></span>  
 <span data-ttu-id="968e1-111">此方法提供了一種確定進程中任何託管物件的完整根鏈的方法，並可用於確定物件仍然處於活動狀態的原因。</span><span class="sxs-lookup"><span data-stu-id="968e1-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="968e1-112">需求</span><span class="sxs-lookup"><span data-stu-id="968e1-112">Requirements</span></span>  
 <span data-ttu-id="968e1-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="968e1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="968e1-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="968e1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="968e1-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="968e1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="968e1-116">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="968e1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="968e1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="968e1-117">See also</span></span>

- [<span data-ttu-id="968e1-118">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="968e1-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="968e1-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="968e1-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
