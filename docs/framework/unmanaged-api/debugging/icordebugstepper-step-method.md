---
title: ICorDebugStepper::Step 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 444390622ca68244661b91dc85814b05556b12a2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493020"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="009be-102">ICorDebugStepper::Step 方法</span><span class="sxs-lookup"><span data-stu-id="009be-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="009be-103">導致此 ICorDebugStepper 單一步驟及其包含的執行緒，以及 （選擇性） 若要繼續單一位逐步執行會在執行緒內呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="009be-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="009be-104">語法</span><span class="sxs-lookup"><span data-stu-id="009be-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="009be-105">參數</span><span class="sxs-lookup"><span data-stu-id="009be-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="009be-106">[in]若要設定`true`逐步執行至呼叫執行緒內的函式。</span><span class="sxs-lookup"><span data-stu-id="009be-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="009be-107">若要設定`false`進入函式。</span><span class="sxs-lookup"><span data-stu-id="009be-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="009be-108">備註</span><span class="sxs-lookup"><span data-stu-id="009be-108">Remarks</span></span>  
 <span data-ttu-id="009be-109">Common language runtime 在這個步進框架中執行下一個 managed 的指令時，就會完成的步驟。</span><span class="sxs-lookup"><span data-stu-id="009be-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="009be-110">如果`Step`是步進上呼叫，這不是在 managed 程式碼、 執行緒所執行的下一個 managed 程式碼指令時，步驟就會完成。</span><span class="sxs-lookup"><span data-stu-id="009be-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="009be-111">需求</span><span class="sxs-lookup"><span data-stu-id="009be-111">Requirements</span></span>  
 <span data-ttu-id="009be-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="009be-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="009be-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="009be-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="009be-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="009be-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="009be-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="009be-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
