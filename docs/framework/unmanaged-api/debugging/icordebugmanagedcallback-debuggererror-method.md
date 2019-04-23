---
title: ICorDebugManagedCallback::DebuggerError 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd7909b94343b1fb83836f5c369ddc1993f049d2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191165"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="8c349-102">ICorDebugManagedCallback::DebuggerError 方法</span><span class="sxs-lookup"><span data-stu-id="8c349-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="8c349-103">錯誤發生在嘗試處理的事件從 common language runtime (CLR) 會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="8c349-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c349-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c349-104">Syntax</span></span>  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c349-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c349-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="8c349-106">[in]表示發生事件的程序的"ICorDebugProcess 」 物件指標。</span><span class="sxs-lookup"><span data-stu-id="8c349-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="8c349-107">[in]從事件處理常式傳回的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="8c349-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="8c349-108">[in]整數，指定 CLR 錯誤。</span><span class="sxs-lookup"><span data-stu-id="8c349-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c349-109">備註</span><span class="sxs-lookup"><span data-stu-id="8c349-109">Remarks</span></span>  
 <span data-ttu-id="8c349-110">此程序可能會放入傳遞模式中，視錯誤的本質而定。</span><span class="sxs-lookup"><span data-stu-id="8c349-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="8c349-111">`DebugError`回呼表示，偵錯服務已停用由於發生錯誤，因此偵錯工具應該提供錯誤訊息給使用者。</span><span class="sxs-lookup"><span data-stu-id="8c349-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="8c349-112">[Icordebugprocess:: Getid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)將會安全地呼叫，但所有其他方法，包括[icordebug:: Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)，不應該呼叫。</span><span class="sxs-lookup"><span data-stu-id="8c349-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="8c349-113">偵錯工具應該使用作業系統的功能，來結束處理序。</span><span class="sxs-lookup"><span data-stu-id="8c349-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c349-114">需求</span><span class="sxs-lookup"><span data-stu-id="8c349-114">Requirements</span></span>  
 <span data-ttu-id="8c349-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c349-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c349-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c349-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c349-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c349-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c349-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c349-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c349-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c349-119">See also</span></span>

- [<span data-ttu-id="8c349-120">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8c349-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
