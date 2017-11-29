---
title: "ICorDebugStepperEnum::Next 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepperEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a0ad2e3361387875178e8261fad4159a3064da1b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="ed051-102">ICorDebugStepperEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="ed051-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="ed051-103">取得 ICorDebugStepper 執行個體的指定的數目從列舉型別，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="ed051-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed051-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed051-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed051-105">參數</span><span class="sxs-lookup"><span data-stu-id="ed051-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ed051-106">[in]數目`ICorDebugStepper`要擷取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ed051-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="ed051-107">[out]陣列的指標，其中每個指向`ICorDebugStepper`物件。</span><span class="sxs-lookup"><span data-stu-id="ed051-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ed051-108">[out]指標的數目`ICorDebugStepper`實際傳回的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ed051-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="ed051-109">這個值可以是 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="ed051-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed051-110">需求</span><span class="sxs-lookup"><span data-stu-id="ed051-110">Requirements</span></span>  
 <span data-ttu-id="ed051-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed051-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed051-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed051-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed051-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed051-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed051-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed051-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
