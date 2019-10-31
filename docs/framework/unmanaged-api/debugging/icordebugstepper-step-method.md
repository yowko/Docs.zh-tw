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
ms.openlocfilehash: 43f86e704e4a52a702b8f563e3c613806eb061b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137523"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="d6020-102">ICorDebugStepper::Step 方法</span><span class="sxs-lookup"><span data-stu-id="d6020-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="d6020-103">使此 ICorDebugStepper 逐步執行其包含的執行緒，並選擇性地繼續透過線上程內呼叫的函式進行單一逐步執行。</span><span class="sxs-lookup"><span data-stu-id="d6020-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6020-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6020-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6020-105">參數</span><span class="sxs-lookup"><span data-stu-id="d6020-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="d6020-106">在設定為 `true`，以逐步執行線上程內呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="d6020-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="d6020-107">設定為 [`false`] 以不進入函式。</span><span class="sxs-lookup"><span data-stu-id="d6020-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6020-108">備註</span><span class="sxs-lookup"><span data-stu-id="d6020-108">Remarks</span></span>  
 <span data-ttu-id="d6020-109">當 common language runtime 在這個分檔器的框架中執行下一個 managed 指令時，就會完成此步驟。</span><span class="sxs-lookup"><span data-stu-id="d6020-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="d6020-110">如果在不是 managed 程式碼的分檔器上呼叫 `Step`，當執行緒執行下一個 managed 程式碼指令時，步驟就會完成。</span><span class="sxs-lookup"><span data-stu-id="d6020-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6020-111">需求</span><span class="sxs-lookup"><span data-stu-id="d6020-111">Requirements</span></span>  
 <span data-ttu-id="d6020-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6020-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6020-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6020-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6020-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6020-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6020-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6020-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
