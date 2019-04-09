---
title: ICorDebugManagedCallback::Breakpoint 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Breakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Breakpoint
helpviewer_keywords:
- ICorDebugManagedCallback::Breakpoint method [.NET Framework debugging]
- Breakpoint method [.NET Framework debugging]
ms.assetid: 60b279b0-a726-46d2-8c53-76986a007ebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8591cb7f8eec3d92100b49db553ed1b5b6533c17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131067"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="f92ec-102">ICorDebugManagedCallback::Breakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="f92ec-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="f92ec-103">遇到中斷點時，請告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="f92ec-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f92ec-104">語法</span><span class="sxs-lookup"><span data-stu-id="f92ec-104">Syntax</span></span>  
  
```  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f92ec-105">參數</span><span class="sxs-lookup"><span data-stu-id="f92ec-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f92ec-106">[in]表示應用程式定義域，其中包含中斷點的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="f92ec-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f92ec-107">[in]ICorDebugThread 物件，表示包含中斷點的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="f92ec-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="f92ec-108">[in]ICorDebugBreakpoint 物件，表示中斷點指標。</span><span class="sxs-lookup"><span data-stu-id="f92ec-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f92ec-109">需求</span><span class="sxs-lookup"><span data-stu-id="f92ec-109">Requirements</span></span>  
 <span data-ttu-id="f92ec-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f92ec-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f92ec-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f92ec-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f92ec-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f92ec-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f92ec-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="f92ec-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f92ec-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f92ec-114">See also</span></span>

- [<span data-ttu-id="f92ec-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f92ec-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
