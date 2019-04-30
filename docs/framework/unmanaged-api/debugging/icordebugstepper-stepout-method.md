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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663f5134cf34bf9beb66da20bbb5886baff5415
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987424"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="e0de1-102">ICorDebugStepper::StepOut 方法</span><span class="sxs-lookup"><span data-stu-id="e0de1-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="e0de1-103">會導致此 ICorDebugStepper 單一步驟透過其包含的執行緒，並完成目前的框架將控制權傳回給呼叫畫面格時。</span><span class="sxs-lookup"><span data-stu-id="e0de1-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0de1-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0de1-104">Syntax</span></span>  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e0de1-105">備註</span><span class="sxs-lookup"><span data-stu-id="e0de1-105">Remarks</span></span>  
 <span data-ttu-id="e0de1-106">A`StepOut`作業才會完成之後從目前的框架正常傳回至呼叫端的框架。</span><span class="sxs-lookup"><span data-stu-id="e0de1-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="e0de1-107">如果`StepOut`時，會呼叫 unmanaged 程式碼，在呼叫它之 managed 程式碼會傳回目前的框架時，會完成的步驟。</span><span class="sxs-lookup"><span data-stu-id="e0de1-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="e0de1-108">在.NET Framework 2.0 版中，請勿使用`StepOut`具有 STOP_UNMANAGED 旗標集因為它將會失敗。</span><span class="sxs-lookup"><span data-stu-id="e0de1-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="e0de1-109">(使用[icordebugstepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)將逐步執行的旗標設定。)Interop 偵錯工具必須跳離函式原生程式碼本身。</span><span class="sxs-lookup"><span data-stu-id="e0de1-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0de1-110">需求</span><span class="sxs-lookup"><span data-stu-id="e0de1-110">Requirements</span></span>  
 <span data-ttu-id="e0de1-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0de1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0de1-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0de1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0de1-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0de1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0de1-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0de1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
