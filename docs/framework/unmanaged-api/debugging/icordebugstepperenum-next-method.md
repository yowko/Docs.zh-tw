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
ms.openlocfilehash: 8bd62e4c5476aacf736f2ddfea008790861d931c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419613"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="292e7-102">ICorDebugStepperEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="292e7-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="292e7-103">取得 ICorDebugStepper 執行個體的指定的數目從列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="292e7-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="292e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="292e7-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="292e7-105">參數</span><span class="sxs-lookup"><span data-stu-id="292e7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="292e7-106">[in]數目`ICorDebugStepper`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="292e7-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="292e7-107">[out]陣列的指標，其中每個指向`ICorDebugStepper`物件。</span><span class="sxs-lookup"><span data-stu-id="292e7-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="292e7-108">[out]指標的數目`ICorDebugStepper`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="292e7-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="292e7-109">這個值可以是 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="292e7-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="292e7-110">需求</span><span class="sxs-lookup"><span data-stu-id="292e7-110">Requirements</span></span>  
 <span data-ttu-id="292e7-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="292e7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="292e7-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="292e7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="292e7-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="292e7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="292e7-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="292e7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
