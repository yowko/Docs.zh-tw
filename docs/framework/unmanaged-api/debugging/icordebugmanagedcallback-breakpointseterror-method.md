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
ms.openlocfilehash: cac8393408de626efe2360999e259780eac29f38
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721331"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="0e27b-102">ICorDebugManagedCallback::BreakpointSetError 方法</span><span class="sxs-lookup"><span data-stu-id="0e27b-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>

<span data-ttu-id="0e27b-103">通知偵錯工具，common language runtime 無法精確地系結函式在函式之前所設定的中斷點， (JIT) 編譯。</span><span class="sxs-lookup"><span data-stu-id="0e27b-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e27b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e27b-104">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e27b-105">參數</span><span class="sxs-lookup"><span data-stu-id="0e27b-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="0e27b-106">在ICorDebugAppDomain 物件的指標，代表包含未系結中斷點的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="0e27b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="0e27b-107">在ICorDebugThread 物件的指標，代表包含未系結中斷點的執行緒。</span><span class="sxs-lookup"><span data-stu-id="0e27b-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="0e27b-108">在ICorDebugBreakpoint 物件的指標，代表未系結的中斷點。</span><span class="sxs-lookup"><span data-stu-id="0e27b-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="0e27b-109">在表示錯誤的整數。</span><span class="sxs-lookup"><span data-stu-id="0e27b-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e27b-110">備註</span><span class="sxs-lookup"><span data-stu-id="0e27b-110">Remarks</span></span>  

 <span data-ttu-id="0e27b-111">將永遠不會叫用指定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="0e27b-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="0e27b-112">偵錯工具應該停用並將它重新系結。</span><span class="sxs-lookup"><span data-stu-id="0e27b-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e27b-113">需求</span><span class="sxs-lookup"><span data-stu-id="0e27b-113">Requirements</span></span>  

 <span data-ttu-id="0e27b-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e27b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e27b-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e27b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e27b-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e27b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e27b-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e27b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e27b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e27b-118">See also</span></span>

- [<span data-ttu-id="0e27b-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0e27b-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
