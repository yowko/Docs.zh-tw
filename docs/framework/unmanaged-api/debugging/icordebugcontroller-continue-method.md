---
title: ICorDebugController::Continue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eacffe5769bc77ab626f6adbc99db1137da565f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749666"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="c4a05-102">ICorDebugController::Continue 方法</span><span class="sxs-lookup"><span data-stu-id="c4a05-102">ICorDebugController::Continue Method</span></span>
<span data-ttu-id="c4a05-103">之後繼續執行的受管理的執行緒呼叫[Stop 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)。</span><span class="sxs-lookup"><span data-stu-id="c4a05-103">Resumes execution of managed threads after a call to [Stop Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a05-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4a05-104">Syntax</span></span>  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4a05-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4a05-105">Parameters</span></span>  
 `fIsOutOfBand`  
 <span data-ttu-id="c4a05-106">[in]設定為`true`如果超出訊號範圍的事件，從繼續執行，否則設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="c4a05-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4a05-107">備註</span><span class="sxs-lookup"><span data-stu-id="c4a05-107">Remarks</span></span>  
 <span data-ttu-id="c4a05-108">`Continue` 若要在呼叫之後繼續進行的程序`ICorDebugController::Stop`方法。</span><span class="sxs-lookup"><span data-stu-id="c4a05-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>  
  
 <span data-ttu-id="c4a05-109">在執行混合模式偵錯時，請勿呼叫`Continue`win32 事件執行緒除非您要繼續從超出訊號範圍的事件。</span><span class="sxs-lookup"><span data-stu-id="c4a05-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>  
  
 <span data-ttu-id="c4a05-110">*頻內事件*managed 的事件或一般的非受控的事件期間偵錯工具支援互動的程序的受管理狀態。</span><span class="sxs-lookup"><span data-stu-id="c4a05-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="c4a05-111">在此情況下，偵錯工具收到[icordebugunmanagedcallback:: Debugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)具有回呼其`fOutOfBand`參數設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="c4a05-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>  
  
 <span data-ttu-id="c4a05-112">*頻外事件*是互動的程序的受管理狀態的期間不可能因為事件而停止處理程序時未受管理的事件。</span><span class="sxs-lookup"><span data-stu-id="c4a05-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="c4a05-113">在此情況下，偵錯工具收到`ICorDebugUnmanagedCallback::DebugEvent`具有回呼其`fOutOfBand`參數設為`true`。</span><span class="sxs-lookup"><span data-stu-id="c4a05-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4a05-114">需求</span><span class="sxs-lookup"><span data-stu-id="c4a05-114">Requirements</span></span>  
 <span data-ttu-id="c4a05-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4a05-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4a05-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4a05-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4a05-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4a05-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4a05-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4a05-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a05-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4a05-119">See also</span></span>
