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
ms.openlocfilehash: 1396e7a8ca61734a9363a9c852502290675249d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727662"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="0b099-102">ICorDebugStepper::StepOut 方法</span><span class="sxs-lookup"><span data-stu-id="0b099-102">ICorDebugStepper::StepOut Method</span></span>

<span data-ttu-id="0b099-103">讓這個 ICorDebugStepper 在其包含的執行緒上執行一次，並在目前的框架將控制權傳回給呼叫的框架時完成。</span><span class="sxs-lookup"><span data-stu-id="0b099-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b099-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b099-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0b099-105">備註</span><span class="sxs-lookup"><span data-stu-id="0b099-105">Remarks</span></span>  

 <span data-ttu-id="0b099-106">`StepOut`從目前的框架傳回至呼叫框架之後，作業將會完成。</span><span class="sxs-lookup"><span data-stu-id="0b099-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="0b099-107">如果 `StepOut` 在非受控程式碼中呼叫，當目前的框架返回呼叫它的 managed 程式碼時，就會完成此步驟。</span><span class="sxs-lookup"><span data-stu-id="0b099-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="0b099-108">在 .NET Framework 2.0 版中，請勿使用 `StepOut` with STOP_UNMANAGED 旗標設定，因為它會失敗。</span><span class="sxs-lookup"><span data-stu-id="0b099-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="0b099-109"> (使用 [ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) 來設定逐步執行的旗標。 ) Interop 偵錯工具必須跳出機器碼本身。</span><span class="sxs-lookup"><span data-stu-id="0b099-109">(Use [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b099-110">需求</span><span class="sxs-lookup"><span data-stu-id="0b099-110">Requirements</span></span>  

 <span data-ttu-id="0b099-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b099-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b099-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b099-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b099-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b099-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b099-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b099-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
