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
ms.openlocfilehash: c2d282e27ec5068fa6fe7f58ba95458fdc219972
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419220"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="5c3f9-102">ICorDebugStepper::Step 方法</span><span class="sxs-lookup"><span data-stu-id="5c3f9-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="5c3f9-103">導致此 ICorDebugStepper 單一步驟其包含的執行緒，以及 （選擇性） 若要繼續逐步執行緒內呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="5c3f9-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c3f9-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c3f9-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c3f9-105">參數</span><span class="sxs-lookup"><span data-stu-id="5c3f9-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="5c3f9-106">[in]設定為`true`逐步執行至呼叫的執行緒內的函式。</span><span class="sxs-lookup"><span data-stu-id="5c3f9-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="5c3f9-107">設定為`false`進入函式。</span><span class="sxs-lookup"><span data-stu-id="5c3f9-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c3f9-108">備註</span><span class="sxs-lookup"><span data-stu-id="5c3f9-108">Remarks</span></span>  
 <span data-ttu-id="5c3f9-109">Common language runtime 會執行下一個 managed 的指令此 stepper 框架中時，就會完成的步驟。</span><span class="sxs-lookup"><span data-stu-id="5c3f9-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="5c3f9-110">如果`Step`是 stepper 上呼叫，不在 managed 程式碼中，步驟將在下一個 managed 程式碼指令由執行緒執行時完成。</span><span class="sxs-lookup"><span data-stu-id="5c3f9-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c3f9-111">需求</span><span class="sxs-lookup"><span data-stu-id="5c3f9-111">Requirements</span></span>  
 <span data-ttu-id="5c3f9-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c3f9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c3f9-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c3f9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c3f9-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c3f9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c3f9-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c3f9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
