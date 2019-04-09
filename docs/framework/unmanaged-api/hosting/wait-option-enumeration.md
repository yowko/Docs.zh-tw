---
title: WAIT_OPTION 列舉
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ac28f28d4d284ba26fadd46e53ebeb8e5b5f3cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139577"
---
# <a name="waitoption-enumeration"></a><span data-ttu-id="09cf8-102">WAIT_OPTION 列舉</span><span class="sxs-lookup"><span data-stu-id="09cf8-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="09cf8-103">包含值，指出是否通用語言執行平台 (CLR) 區塊所要求的作業，應該採取動作的主機。</span><span class="sxs-lookup"><span data-stu-id="09cf8-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09cf8-104">語法</span><span class="sxs-lookup"><span data-stu-id="09cf8-104">Syntax</span></span>  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="09cf8-105">成員</span><span class="sxs-lookup"><span data-stu-id="09cf8-105">Members</span></span>  
  
|<span data-ttu-id="09cf8-106">成員</span><span class="sxs-lookup"><span data-stu-id="09cf8-106">Member</span></span>|<span data-ttu-id="09cf8-107">描述</span><span class="sxs-lookup"><span data-stu-id="09cf8-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="09cf8-108">主應用程式應該喚醒工作，如果 CLR 會呼叫[ihosttask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="09cf8-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="09cf8-109">主應用程式，它就必須提取目前的 OS 執行緒上的訊息，如果執行緒被封鎖。</span><span class="sxs-lookup"><span data-stu-id="09cf8-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="09cf8-110">執行階段會指定此值只在<xref:System.Threading.ApartmentState.STA>執行緒。</span><span class="sxs-lookup"><span data-stu-id="09cf8-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="09cf8-111">通知主機指定的同步處理的要求不會中斷由主應用程式。</span><span class="sxs-lookup"><span data-stu-id="09cf8-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="09cf8-112">也就是說，無法傳回主機`HOST_E_DEADLOCK`。</span><span class="sxs-lookup"><span data-stu-id="09cf8-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09cf8-113">備註</span><span class="sxs-lookup"><span data-stu-id="09cf8-113">Remarks</span></span>  
 <span data-ttu-id="09cf8-114">[Ihosttaskmanager:: Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)並[ihosttaskmanager:: Switchtotask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)方法都採用這種類型的參數。</span><span class="sxs-lookup"><span data-stu-id="09cf8-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09cf8-115">需求</span><span class="sxs-lookup"><span data-stu-id="09cf8-115">Requirements</span></span>  
 <span data-ttu-id="09cf8-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09cf8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09cf8-117">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="09cf8-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09cf8-118">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="09cf8-118">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="09cf8-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="09cf8-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="09cf8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09cf8-120">See also</span></span>

- [<span data-ttu-id="09cf8-121">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="09cf8-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
