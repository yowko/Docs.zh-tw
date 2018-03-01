---
title: "ICorDebugManagedCallback::Breakpoint 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d7b0c521f1b2c5a2c258738239696ad48d4e9350
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="29988-102">ICorDebugManagedCallback::Breakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="29988-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="29988-103">遇到中斷點時，請告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="29988-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29988-104">語法</span><span class="sxs-lookup"><span data-stu-id="29988-104">Syntax</span></span>  
  
```  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29988-105">參數</span><span class="sxs-lookup"><span data-stu-id="29988-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="29988-106">[in]表示應用程式定義域，其中包含中斷點的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="29988-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="29988-107">[in]表示包含中斷點的執行緒 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="29988-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="29988-108">[in]ICorDebugBreakpoint 物件，表示中斷點指標。</span><span class="sxs-lookup"><span data-stu-id="29988-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29988-109">需求</span><span class="sxs-lookup"><span data-stu-id="29988-109">Requirements</span></span>  
 <span data-ttu-id="29988-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29988-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29988-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29988-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29988-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29988-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29988-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29988-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29988-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="29988-114">See Also</span></span>  
 [<span data-ttu-id="29988-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="29988-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
