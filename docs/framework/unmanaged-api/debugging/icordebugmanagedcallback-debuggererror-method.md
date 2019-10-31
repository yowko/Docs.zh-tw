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
ms.openlocfilehash: c03be2405e1ab0287a2921b6e2e293862c67a193
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137379"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="6941e-102">ICorDebugManagedCallback::DebuggerError 方法</span><span class="sxs-lookup"><span data-stu-id="6941e-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="6941e-103">通知偵錯工具，在嘗試處理來自 common language runtime （CLR）的事件時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6941e-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6941e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6941e-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6941e-105">參數</span><span class="sxs-lookup"><span data-stu-id="6941e-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="6941e-106">在代表發生事件之進程的 "ICorDebugProcess" 物件指標。</span><span class="sxs-lookup"><span data-stu-id="6941e-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="6941e-107">在從事件處理常式傳回的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="6941e-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="6941e-108">在指定 CLR 錯誤的整數。</span><span class="sxs-lookup"><span data-stu-id="6941e-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6941e-109">備註</span><span class="sxs-lookup"><span data-stu-id="6941e-109">Remarks</span></span>  
 <span data-ttu-id="6941e-110">視錯誤的性質而定，此程式可能會置於傳遞模式。</span><span class="sxs-lookup"><span data-stu-id="6941e-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="6941e-111">`DebugError` 回呼表示因為發生錯誤而停用了偵錯工具，因此偵錯工具應該將錯誤訊息提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="6941e-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="6941e-112">[ICorDebugProcess：： GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)可放心呼叫，但不應呼叫所有其他方法，包括[ICorDebug：： Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)。</span><span class="sxs-lookup"><span data-stu-id="6941e-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="6941e-113">偵錯工具應該使用作業系統功能來終止進程。</span><span class="sxs-lookup"><span data-stu-id="6941e-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6941e-114">需求</span><span class="sxs-lookup"><span data-stu-id="6941e-114">Requirements</span></span>  
 <span data-ttu-id="6941e-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6941e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6941e-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6941e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6941e-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6941e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6941e-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6941e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6941e-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="6941e-119">See also</span></span>

- [<span data-ttu-id="6941e-120">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6941e-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
