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
ms.openlocfilehash: 381fdecfb2cb194cd1eb00a5b55db6fb89eeebbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413913"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="8e421-102">ICorDebugManagedCallback::Breakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="8e421-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="8e421-103">遇到中斷點時，請告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="8e421-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e421-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e421-104">Syntax</span></span>  
  
```  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e421-105">參數</span><span class="sxs-lookup"><span data-stu-id="8e421-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="8e421-106">[in]表示應用程式定義域，其中包含中斷點的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="8e421-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="8e421-107">[in]表示包含中斷點的執行緒 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="8e421-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="8e421-108">[in]ICorDebugBreakpoint 物件，表示中斷點指標。</span><span class="sxs-lookup"><span data-stu-id="8e421-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e421-109">需求</span><span class="sxs-lookup"><span data-stu-id="8e421-109">Requirements</span></span>  
 <span data-ttu-id="8e421-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e421-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e421-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e421-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e421-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e421-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e421-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e421-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e421-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e421-114">See Also</span></span>  
 [<span data-ttu-id="8e421-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8e421-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
