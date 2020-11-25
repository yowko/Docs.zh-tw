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
ms.openlocfilehash: 234705e4495a1a582f3801ad1e645f923cd6f4b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727688"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="3358b-102">ICorDebugStepper::Step 方法</span><span class="sxs-lookup"><span data-stu-id="3358b-102">ICorDebugStepper::Step Method</span></span>

<span data-ttu-id="3358b-103">讓這個 ICorDebugStepper 能以單一步驟完成其包含的執行緒，並選擇性地透過線上程中呼叫的函式繼續進行單一逐步執行。</span><span class="sxs-lookup"><span data-stu-id="3358b-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3358b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3358b-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3358b-105">參數</span><span class="sxs-lookup"><span data-stu-id="3358b-105">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="3358b-106">在將設定為，逐步執行在 `true` 執行緒中呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="3358b-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="3358b-107">設定為 `false` 以不進入函數。</span><span class="sxs-lookup"><span data-stu-id="3358b-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3358b-108">備註</span><span class="sxs-lookup"><span data-stu-id="3358b-108">Remarks</span></span>  

 <span data-ttu-id="3358b-109">當 common language runtime 在這個分檔器的框架中執行下一個 managed 指令時，會完成此步驟。</span><span class="sxs-lookup"><span data-stu-id="3358b-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="3358b-110">如果 `Step` 在不在 managed 程式碼中的分檔器上呼叫，則會線上程執行下一個 managed 程式碼指令時完成此步驟。</span><span class="sxs-lookup"><span data-stu-id="3358b-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3358b-111">需求</span><span class="sxs-lookup"><span data-stu-id="3358b-111">Requirements</span></span>  

 <span data-ttu-id="3358b-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3358b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3358b-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3358b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3358b-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3358b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3358b-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3358b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
