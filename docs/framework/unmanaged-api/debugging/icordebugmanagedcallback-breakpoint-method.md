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
ms.openlocfilehash: ac91a9c662a82c5ab870d01cb4b5d87c7af6b6ba
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782079"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="60152-102">ICorDebugManagedCallback::Breakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="60152-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="60152-103">遇到中斷點時，通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="60152-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60152-104">語法</span><span class="sxs-lookup"><span data-stu-id="60152-104">Syntax</span></span>  
  
```cpp  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60152-105">參數</span><span class="sxs-lookup"><span data-stu-id="60152-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="60152-106">在ICorDebugAppDomain 物件的指標，表示包含中斷點的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="60152-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="60152-107">在ICorDebugThread 物件的指標，表示包含中斷點的執行緒。</span><span class="sxs-lookup"><span data-stu-id="60152-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="60152-108">在代表中斷點之 ICorDebugBreakpoint 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="60152-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60152-109">需求</span><span class="sxs-lookup"><span data-stu-id="60152-109">Requirements</span></span>  
 <span data-ttu-id="60152-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60152-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60152-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60152-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60152-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60152-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60152-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60152-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60152-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="60152-114">See also</span></span>

- [<span data-ttu-id="60152-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="60152-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
