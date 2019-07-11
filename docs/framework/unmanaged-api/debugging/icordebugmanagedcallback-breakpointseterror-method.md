---
title: ICorDebugManagedCallback::BreakpointSetError 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3ef4b284676608363281e04087f6435dcb1ef74
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759848"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="49829-102">ICorDebugManagedCallback::BreakpointSetError 方法</span><span class="sxs-lookup"><span data-stu-id="49829-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="49829-103">Common language runtime 無法精確地繫結之前的函式是在 just-in-time (JIT) 編譯，並設定中斷點會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="49829-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49829-104">語法</span><span class="sxs-lookup"><span data-stu-id="49829-104">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49829-105">參數</span><span class="sxs-lookup"><span data-stu-id="49829-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="49829-106">[in]ICorDebugAppDomain 物件，表示應用程式定義域，其中包含未繫結的中斷點指標。</span><span class="sxs-lookup"><span data-stu-id="49829-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="49829-107">[in]ICorDebugThread 物件，表示包含未繫結的中斷點的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="49829-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="49829-108">[in]ICorDebugBreakpoint 物件，表示未繫結的中斷點指標。</span><span class="sxs-lookup"><span data-stu-id="49829-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="49829-109">[in]整數，表示錯誤。</span><span class="sxs-lookup"><span data-stu-id="49829-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49829-110">備註</span><span class="sxs-lookup"><span data-stu-id="49829-110">Remarks</span></span>  
 <span data-ttu-id="49829-111">永遠不會叫用指定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="49829-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="49829-112">偵錯工具應該停用，並將它重新繫結。</span><span class="sxs-lookup"><span data-stu-id="49829-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49829-113">需求</span><span class="sxs-lookup"><span data-stu-id="49829-113">Requirements</span></span>  
 <span data-ttu-id="49829-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49829-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49829-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49829-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49829-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49829-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49829-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49829-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49829-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49829-118">See also</span></span>

- [<span data-ttu-id="49829-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="49829-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
