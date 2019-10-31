---
title: EClrEvent 列舉
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: ee749fd40f440e92f1d1b09c2ea5e7bdd51f1cbe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131139"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="12a63-102">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="12a63-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="12a63-103">描述主機可以註冊回呼的 common language runtime （CLR）事件。</span><span class="sxs-lookup"><span data-stu-id="12a63-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a63-104">語法</span><span class="sxs-lookup"><span data-stu-id="12a63-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="12a63-105">Members</span><span class="sxs-lookup"><span data-stu-id="12a63-105">Members</span></span>  
  
|<span data-ttu-id="12a63-106">成員</span><span class="sxs-lookup"><span data-stu-id="12a63-106">Member</span></span>|<span data-ttu-id="12a63-107">描述</span><span class="sxs-lookup"><span data-stu-id="12a63-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="12a63-108">指定嚴重的 CLR 錯誤。</span><span class="sxs-lookup"><span data-stu-id="12a63-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="12a63-109">指定特定 <xref:System.AppDomain>的卸載。</span><span class="sxs-lookup"><span data-stu-id="12a63-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="12a63-110">指定已產生 Managed 偵錯工具（MDA）訊息。</span><span class="sxs-lookup"><span data-stu-id="12a63-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="12a63-111">指定發生堆疊溢位錯誤。</span><span class="sxs-lookup"><span data-stu-id="12a63-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12a63-112">備註</span><span class="sxs-lookup"><span data-stu-id="12a63-112">Remarks</span></span>  
 <span data-ttu-id="12a63-113">主機可以藉由呼叫[ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)介面的方法，為 `EClrEvent` 所描述的任何事件種類註冊回呼。</span><span class="sxs-lookup"><span data-stu-id="12a63-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="12a63-114">主機會藉由呼叫[ICLRControl：： GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法來取得這個介面的指標。</span><span class="sxs-lookup"><span data-stu-id="12a63-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="12a63-115">`Event_CLRDisabled` 和 `Event_DomainUnload` 事件可以引發一次以上，並從不同的執行緒發出，以表示卸載或停用 CLR。</span><span class="sxs-lookup"><span data-stu-id="12a63-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="12a63-116">`Event_MDAFired` 事件會引發[MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)實例的建立，其中包含 MDA 訊息的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="12a63-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="12a63-117">如需有關 Mda 的詳細資訊，請參閱[診斷 Managed 偵錯工具的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。</span><span class="sxs-lookup"><span data-stu-id="12a63-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12a63-118">需求</span><span class="sxs-lookup"><span data-stu-id="12a63-118">Requirements</span></span>  
 <span data-ttu-id="12a63-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12a63-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12a63-120">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="12a63-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="12a63-121">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="12a63-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12a63-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12a63-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a63-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="12a63-123">See also</span></span>

- [<span data-ttu-id="12a63-124">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="12a63-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="12a63-125">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="12a63-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="12a63-126">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="12a63-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
