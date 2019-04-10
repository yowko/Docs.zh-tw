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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13d564be68d6b49a1616be97710312f33f828d48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176341"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="35a9f-102">EClrEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="35a9f-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="35a9f-103">描述通用語言執行平台 (CLR) 事件，主機可以註冊的回呼。</span><span class="sxs-lookup"><span data-stu-id="35a9f-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35a9f-104">語法</span><span class="sxs-lookup"><span data-stu-id="35a9f-104">Syntax</span></span>  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="35a9f-105">成員</span><span class="sxs-lookup"><span data-stu-id="35a9f-105">Members</span></span>  
  
|<span data-ttu-id="35a9f-106">成員</span><span class="sxs-lookup"><span data-stu-id="35a9f-106">Member</span></span>|<span data-ttu-id="35a9f-107">描述</span><span class="sxs-lookup"><span data-stu-id="35a9f-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="35a9f-108">指定嚴重的 CLR 錯誤。</span><span class="sxs-lookup"><span data-stu-id="35a9f-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="35a9f-109">指定特定的卸載<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="35a9f-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="35a9f-110">指定已產生 Managed 偵錯助理 (MDA) 訊息。</span><span class="sxs-lookup"><span data-stu-id="35a9f-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="35a9f-111">指定發生堆疊溢位錯誤。</span><span class="sxs-lookup"><span data-stu-id="35a9f-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35a9f-112">備註</span><span class="sxs-lookup"><span data-stu-id="35a9f-112">Remarks</span></span>  
 <span data-ttu-id="35a9f-113">主機可以註冊的任何事件類型所描述的回呼`EClrEvent`藉由呼叫的方法[ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="35a9f-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="35a9f-114">主機取得這個介面的指標，藉由呼叫[iclrcontrol:: Getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="35a9f-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="35a9f-115">`Event_CLRDisabled`和`Event_DomainUnload`可以引發事件，一次以上，並從不同的執行緒，以表示卸載或 CLR 的停用。</span><span class="sxs-lookup"><span data-stu-id="35a9f-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="35a9f-116">`Event_MDAFired`事件引發建立[MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)包含 MDA 訊息的詳細資料的執行個體。</span><span class="sxs-lookup"><span data-stu-id="35a9f-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="35a9f-117">如需有關 Mda 的詳細資訊，請參閱 < [Managed 偵錯助理診斷錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。</span><span class="sxs-lookup"><span data-stu-id="35a9f-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35a9f-118">需求</span><span class="sxs-lookup"><span data-stu-id="35a9f-118">Requirements</span></span>  
 <span data-ttu-id="35a9f-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35a9f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35a9f-120">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="35a9f-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35a9f-121">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="35a9f-121">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="35a9f-122">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="35a9f-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35a9f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35a9f-123">See also</span></span>

- [<span data-ttu-id="35a9f-124">IActionOnCLREvent 介面</span><span class="sxs-lookup"><span data-stu-id="35a9f-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="35a9f-125">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="35a9f-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="35a9f-126">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="35a9f-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
