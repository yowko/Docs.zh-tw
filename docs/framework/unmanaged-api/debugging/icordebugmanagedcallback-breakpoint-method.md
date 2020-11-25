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
ms.openlocfilehash: d7cf966f407572cc681f641b63791906a5c015f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731861"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="a6af5-102">ICorDebugManagedCallback::Breakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="a6af5-102">ICorDebugManagedCallback::Breakpoint Method</span></span>

<span data-ttu-id="a6af5-103">在遇到中斷點時通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a6af5-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6af5-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6af5-104">Syntax</span></span>  
  
```cpp  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6af5-105">參數</span><span class="sxs-lookup"><span data-stu-id="a6af5-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="a6af5-106">在ICorDebugAppDomain 物件的指標，代表包含中斷點的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="a6af5-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a6af5-107">在代表包含中斷點之執行緒的 ICorDebugThread 物件指標。</span><span class="sxs-lookup"><span data-stu-id="a6af5-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="a6af5-108">在代表中斷點之 ICorDebugBreakpoint 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="a6af5-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6af5-109">需求</span><span class="sxs-lookup"><span data-stu-id="a6af5-109">Requirements</span></span>  

 <span data-ttu-id="a6af5-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6af5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6af5-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6af5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6af5-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6af5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6af5-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6af5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6af5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6af5-114">See also</span></span>

- [<span data-ttu-id="a6af5-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a6af5-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
