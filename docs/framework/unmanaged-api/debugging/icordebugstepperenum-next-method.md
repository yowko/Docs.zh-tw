---
title: ICorDebugStepperEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58f148eb4c3206ba12eed41df670846d7beab77a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771632"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="0bc28-102">ICorDebugStepperEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="0bc28-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="0bc28-103">取得指定的 ICorDebugStepper 執行個體的數目從列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="0bc28-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc28-104">語法</span><span class="sxs-lookup"><span data-stu-id="0bc28-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bc28-105">參數</span><span class="sxs-lookup"><span data-stu-id="0bc28-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0bc28-106">[in]數目`ICorDebugStepper`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0bc28-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="0bc28-107">[out]指標的陣列，其中每一個指向`ICorDebugStepper`物件。</span><span class="sxs-lookup"><span data-stu-id="0bc28-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0bc28-108">[out]數目的指標`ICorDebugStepper`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0bc28-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="0bc28-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="0bc28-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bc28-110">需求</span><span class="sxs-lookup"><span data-stu-id="0bc28-110">Requirements</span></span>  
 <span data-ttu-id="0bc28-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0bc28-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bc28-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bc28-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bc28-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bc28-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bc28-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bc28-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
