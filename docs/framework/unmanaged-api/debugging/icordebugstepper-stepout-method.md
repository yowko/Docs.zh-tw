---
title: ICorDebugStepper::StepOut 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: 08cf2d0bb09080296fc1fcc69b5817f4d6118765
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791719"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="5a86d-102">ICorDebugStepper::StepOut 方法</span><span class="sxs-lookup"><span data-stu-id="5a86d-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="5a86d-103">使此 ICorDebugStepper 逐步執行其包含的執行緒，並在目前的框架將控制項傳回至呼叫的框架時完成。</span><span class="sxs-lookup"><span data-stu-id="5a86d-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a86d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a86d-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5a86d-105">備註</span><span class="sxs-lookup"><span data-stu-id="5a86d-105">Remarks</span></span>  
 <span data-ttu-id="5a86d-106">`StepOut` 作業會在從目前的框架正常傳回至呼叫框架之後完成。</span><span class="sxs-lookup"><span data-stu-id="5a86d-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="5a86d-107">如果在非受控碼中呼叫 `StepOut`，當目前的框架回到呼叫它的 managed 程式碼時，步驟就會完成。</span><span class="sxs-lookup"><span data-stu-id="5a86d-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="5a86d-108">在 .NET Framework 版本2.0 中，請勿使用已設定 STOP_UNMANAGED 旗標的 `StepOut`，因為它將會失敗。</span><span class="sxs-lookup"><span data-stu-id="5a86d-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="5a86d-109">（使用[ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md)來設定逐步執行的旗標）。Interop 偵錯工具必須以機器碼本身的模式執行。</span><span class="sxs-lookup"><span data-stu-id="5a86d-109">(Use [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a86d-110">需求</span><span class="sxs-lookup"><span data-stu-id="5a86d-110">Requirements</span></span>  
 <span data-ttu-id="5a86d-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a86d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a86d-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a86d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a86d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a86d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a86d-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a86d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
