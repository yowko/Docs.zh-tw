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
ms.openlocfilehash: 67f3e63b58e08a4b9ccfbd555e6edcdef0d00d90
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688928"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="c34f4-102">ICorDebugManagedCallback::ExitProcess 方法</span><span class="sxs-lookup"><span data-stu-id="c34f4-102">ICorDebugManagedCallback::ExitProcess Method</span></span>

<span data-ttu-id="c34f4-103">通知偵錯工具已結束。</span><span class="sxs-lookup"><span data-stu-id="c34f4-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c34f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="c34f4-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c34f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="c34f4-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="c34f4-106">在表示處理常式之 ICorDebugProcess 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="c34f4-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c34f4-107">備註</span><span class="sxs-lookup"><span data-stu-id="c34f4-107">Remarks</span></span>  

 <span data-ttu-id="c34f4-108">您無法從事件繼續進行 `ExitProcess` 。</span><span class="sxs-lookup"><span data-stu-id="c34f4-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="c34f4-109">此事件可能會以非同步方式引發到其他事件，而進程則會停止。</span><span class="sxs-lookup"><span data-stu-id="c34f4-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="c34f4-110">如果進程在停止時終止（通常是因為某些外部強制），就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="c34f4-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="c34f4-111">如果 common language runtime (CLR) 已經分派 managed 回呼，此事件將會延遲到回呼傳回之後。</span><span class="sxs-lookup"><span data-stu-id="c34f4-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="c34f4-112">`ExitProcess`事件是唯一保證會在關機時呼叫的 exit/unload 事件。</span><span class="sxs-lookup"><span data-stu-id="c34f4-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c34f4-113">需求</span><span class="sxs-lookup"><span data-stu-id="c34f4-113">Requirements</span></span>  

 <span data-ttu-id="c34f4-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c34f4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c34f4-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c34f4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c34f4-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c34f4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c34f4-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c34f4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c34f4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c34f4-118">See also</span></span>

- [<span data-ttu-id="c34f4-119">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c34f4-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
