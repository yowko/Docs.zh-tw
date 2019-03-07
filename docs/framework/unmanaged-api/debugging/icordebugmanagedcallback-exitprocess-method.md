---
title: ICorDebugManagedCallback::ExitProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b33b38b85bd5b8cfb3502e3fadcd739aac37b2dc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476369"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="07d54-102">ICorDebugManagedCallback::ExitProcess 方法</span><span class="sxs-lookup"><span data-stu-id="07d54-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="07d54-103">告知偵錯工具的處理序已結束。</span><span class="sxs-lookup"><span data-stu-id="07d54-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07d54-104">語法</span><span class="sxs-lookup"><span data-stu-id="07d54-104">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07d54-105">參數</span><span class="sxs-lookup"><span data-stu-id="07d54-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="07d54-106">[in]ICorDebugProcess 物件代表處理程序的指標。</span><span class="sxs-lookup"><span data-stu-id="07d54-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07d54-107">備註</span><span class="sxs-lookup"><span data-stu-id="07d54-107">Remarks</span></span>  
 <span data-ttu-id="07d54-108">您無法繼續從`ExitProcess`事件。</span><span class="sxs-lookup"><span data-stu-id="07d54-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="07d54-109">其他事件，而要停止的程序會出現此事件可能會以非同步方式引發。</span><span class="sxs-lookup"><span data-stu-id="07d54-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="07d54-110">如果在處理序終止時停止，通常是因為某些外部人力，也可能會發生。</span><span class="sxs-lookup"><span data-stu-id="07d54-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="07d54-111">如果 common language runtime (CLR) 已分派 managed 回撥，則此事件將會延遲，直到該回呼傳回後。</span><span class="sxs-lookup"><span data-stu-id="07d54-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="07d54-112">`ExitProcess`事件是唯一的結束/卸載事件保證會呼叫關閉。</span><span class="sxs-lookup"><span data-stu-id="07d54-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07d54-113">需求</span><span class="sxs-lookup"><span data-stu-id="07d54-113">Requirements</span></span>  
 <span data-ttu-id="07d54-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07d54-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07d54-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07d54-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07d54-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07d54-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07d54-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07d54-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d54-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07d54-118">See also</span></span>
- [<span data-ttu-id="07d54-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="07d54-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
