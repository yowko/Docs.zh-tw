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
ms.openlocfilehash: d8e62499a813419ecc30924624da553ca9f2c7b2
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213396"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="73ff7-102">ICorDebugManagedCallback::Breakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="73ff7-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="73ff7-103">遇到中斷點時，通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="73ff7-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73ff7-104">語法</span><span class="sxs-lookup"><span data-stu-id="73ff7-104">Syntax</span></span>  
  
```cpp  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73ff7-105">參數</span><span class="sxs-lookup"><span data-stu-id="73ff7-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="73ff7-106">在ICorDebugAppDomain 物件的指標，表示包含中斷點的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="73ff7-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="73ff7-107">在ICorDebugThread 物件的指標，表示包含中斷點的執行緒。</span><span class="sxs-lookup"><span data-stu-id="73ff7-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="73ff7-108">在代表中斷點之 ICorDebugBreakpoint 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="73ff7-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73ff7-109">需求</span><span class="sxs-lookup"><span data-stu-id="73ff7-109">Requirements</span></span>  
 <span data-ttu-id="73ff7-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73ff7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73ff7-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73ff7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73ff7-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73ff7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73ff7-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73ff7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ff7-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="73ff7-114">See also</span></span>

- [<span data-ttu-id="73ff7-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="73ff7-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
