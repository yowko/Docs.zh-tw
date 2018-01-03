---
title: "ICorDebugManagedCallback::DebuggerError 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.DebuggerError
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc92bc6a1718d9d3505443e5b13786d1a359481f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="cfb96-102">ICorDebugManagedCallback::DebuggerError 方法</span><span class="sxs-lookup"><span data-stu-id="cfb96-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="cfb96-103">告知偵錯工具嘗試處理從 common language runtime (CLR) 事件時，已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="cfb96-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfb96-104">語法</span><span class="sxs-lookup"><span data-stu-id="cfb96-104">Syntax</span></span>  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfb96-105">參數</span><span class="sxs-lookup"><span data-stu-id="cfb96-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="cfb96-106">[in]代表發生事件的程序 」 ICorDebugProcess 」 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="cfb96-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="cfb96-107">[in]從事件處理常式傳回的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="cfb96-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="cfb96-108">[in]指定 CLR 錯誤的整數。</span><span class="sxs-lookup"><span data-stu-id="cfb96-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfb96-109">備註</span><span class="sxs-lookup"><span data-stu-id="cfb96-109">Remarks</span></span>  
 <span data-ttu-id="cfb96-110">處理程序可能會放置於傳遞模式，視錯誤的本質而定。</span><span class="sxs-lookup"><span data-stu-id="cfb96-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="cfb96-111">`DebugError`回呼表示，偵錯服務已停用由於發生錯誤，因此偵錯工具應該提供錯誤訊息給使用者。</span><span class="sxs-lookup"><span data-stu-id="cfb96-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="cfb96-112">[Icordebugprocess:: Getid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)會安全地呼叫，但所有其他方法，包括[icordebug:: Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)，不應呼叫。</span><span class="sxs-lookup"><span data-stu-id="cfb96-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="cfb96-113">偵錯工具應該使用作業系統的功能，來結束處理序。</span><span class="sxs-lookup"><span data-stu-id="cfb96-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfb96-114">需求</span><span class="sxs-lookup"><span data-stu-id="cfb96-114">Requirements</span></span>  
 <span data-ttu-id="cfb96-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cfb96-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfb96-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfb96-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfb96-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfb96-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfb96-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfb96-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb96-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="cfb96-119">See Also</span></span>  
 [<span data-ttu-id="cfb96-120">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="cfb96-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
