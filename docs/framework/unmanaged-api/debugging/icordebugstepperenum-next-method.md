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
ms.openlocfilehash: 11d9c7393827b613d49e23972b4896bfe657a544
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138979"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="278f4-102">ICorDebugStepperEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="278f4-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="278f4-103">從列舉中取得指定數目的 ICorDebugStepper 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="278f4-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="278f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="278f4-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="278f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="278f4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="278f4-106">在要抓取 `ICorDebugStepper` 實例的數目。</span><span class="sxs-lookup"><span data-stu-id="278f4-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="278f4-107">脫銷指標陣列，其中每一個都會指向 `ICorDebugStepper` 物件。</span><span class="sxs-lookup"><span data-stu-id="278f4-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="278f4-108">脫銷實際傳回的 `ICorDebugStepper` 實例數目的指標。</span><span class="sxs-lookup"><span data-stu-id="278f4-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="278f4-109">如果 `celt` 是一個，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="278f4-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="278f4-110">需求</span><span class="sxs-lookup"><span data-stu-id="278f4-110">Requirements</span></span>  
 <span data-ttu-id="278f4-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="278f4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="278f4-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="278f4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="278f4-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="278f4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="278f4-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="278f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
