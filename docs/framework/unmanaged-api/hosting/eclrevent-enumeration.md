---
title: "EClrEvent 列舉"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d453cf7d3c7613397890c2d49a2dbe81a2e5d81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="e318d-102">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="e318d-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="e318d-103">描述 common language runtime (CLR) 事件，主機可以註冊的回呼。</span><span class="sxs-lookup"><span data-stu-id="e318d-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e318d-104">語法</span><span class="sxs-lookup"><span data-stu-id="e318d-104">Syntax</span></span>  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="e318d-105">成員</span><span class="sxs-lookup"><span data-stu-id="e318d-105">Members</span></span>  
  
|<span data-ttu-id="e318d-106">成員</span><span class="sxs-lookup"><span data-stu-id="e318d-106">Member</span></span>|<span data-ttu-id="e318d-107">描述</span><span class="sxs-lookup"><span data-stu-id="e318d-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="e318d-108">指定 CLR 嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="e318d-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="e318d-109">指定特定的卸載<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="e318d-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="e318d-110">指定已產生的 Managed 偵錯助理 (MDA) 訊息。</span><span class="sxs-lookup"><span data-stu-id="e318d-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="e318d-111">指定發生堆疊溢位錯誤。</span><span class="sxs-lookup"><span data-stu-id="e318d-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e318d-112">備註</span><span class="sxs-lookup"><span data-stu-id="e318d-112">Remarks</span></span>  
 <span data-ttu-id="e318d-113">主機可以註冊任何所描述的事件類型的回呼`EClrEvent`藉由呼叫的方法[ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="e318d-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="e318d-114">主機取得此介面的指標，藉由呼叫[iclrcontrol:: Getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e318d-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="e318d-115">`Event_CLRDisabled`和`Event_DomainUnload`可以引發事件，一次以上，從不同的執行緒，以便通知卸載或 CLR 的停用。</span><span class="sxs-lookup"><span data-stu-id="e318d-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="e318d-116">`Event_MDAFired`事件引發建立[MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)包含 MDA 訊息的詳細資料的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e318d-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="e318d-117">如需 Mda 的詳細資訊，請參閱[診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。</span><span class="sxs-lookup"><span data-stu-id="e318d-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e318d-118">需求</span><span class="sxs-lookup"><span data-stu-id="e318d-118">Requirements</span></span>  
 <span data-ttu-id="e318d-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e318d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e318d-120">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e318d-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e318d-121">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e318d-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e318d-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e318d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e318d-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="e318d-123">See Also</span></span>  
 [<span data-ttu-id="e318d-124">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="e318d-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="e318d-125">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="e318d-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="e318d-126">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="e318d-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
