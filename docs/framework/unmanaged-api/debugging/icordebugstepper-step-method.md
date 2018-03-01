---
title: "ICorDebugStepper::Step 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f921725d6794f08530a537462208264ced1dc089
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="69cfe-102">ICorDebugStepper::Step 方法</span><span class="sxs-lookup"><span data-stu-id="69cfe-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="69cfe-103">導致此 ICorDebugStepper 單一步驟其包含的執行緒，以及 （選擇性） 若要繼續逐步執行緒內呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="69cfe-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69cfe-104">語法</span><span class="sxs-lookup"><span data-stu-id="69cfe-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69cfe-105">參數</span><span class="sxs-lookup"><span data-stu-id="69cfe-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="69cfe-106">[in]設定為`true`逐步執行至呼叫的執行緒內的函式。</span><span class="sxs-lookup"><span data-stu-id="69cfe-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="69cfe-107">設定為`false`進入函式。</span><span class="sxs-lookup"><span data-stu-id="69cfe-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69cfe-108">備註</span><span class="sxs-lookup"><span data-stu-id="69cfe-108">Remarks</span></span>  
 <span data-ttu-id="69cfe-109">Common language runtime 會執行下一個 managed 的指令此 stepper 框架中時，就會完成的步驟。</span><span class="sxs-lookup"><span data-stu-id="69cfe-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="69cfe-110">如果`Step`是 stepper 上呼叫，不在 managed 程式碼中，步驟將在下一個 managed 程式碼指令由執行緒執行時完成。</span><span class="sxs-lookup"><span data-stu-id="69cfe-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69cfe-111">需求</span><span class="sxs-lookup"><span data-stu-id="69cfe-111">Requirements</span></span>  
 <span data-ttu-id="69cfe-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69cfe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69cfe-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69cfe-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69cfe-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69cfe-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69cfe-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69cfe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
