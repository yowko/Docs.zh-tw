---
title: "WAIT_OPTION 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: WAIT_OPTION
api_location: mscoree.dll
api_type: COM
f1_keywords: WAIT_OPTION
helpviewer_keywords: WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 08bdfc928c56d144f50399814a81795fea74574a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="waitoption-enumeration"></a><span data-ttu-id="eb380-102">WAIT_OPTION 列舉</span><span class="sxs-lookup"><span data-stu-id="eb380-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="eb380-103">包含值，表示是否通用語言執行平台 (CLR) 區塊所要求的作業，應該採取動作的主機。</span><span class="sxs-lookup"><span data-stu-id="eb380-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb380-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb380-104">Syntax</span></span>  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="eb380-105">成員</span><span class="sxs-lookup"><span data-stu-id="eb380-105">Members</span></span>  
  
|<span data-ttu-id="eb380-106">成員</span><span class="sxs-lookup"><span data-stu-id="eb380-106">Member</span></span>|<span data-ttu-id="eb380-107">說明</span><span class="sxs-lookup"><span data-stu-id="eb380-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="eb380-108">通知主機應該喚醒工作，如果 CLR 會呼叫[ihosttask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="eb380-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="eb380-109">通知主機，它就必須提示上目前的作業系統執行緒的訊息，如果執行緒被封鎖。</span><span class="sxs-lookup"><span data-stu-id="eb380-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="eb380-110">執行階段指定這個值只在<xref:System.Threading.ApartmentState.STA>執行緒。</span><span class="sxs-lookup"><span data-stu-id="eb380-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="eb380-111">通知主機指定的同步處理要求，無法分類的主機。</span><span class="sxs-lookup"><span data-stu-id="eb380-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="eb380-112">也就是說，無法傳回主機`HOST_E_DEADLOCK`。</span><span class="sxs-lookup"><span data-stu-id="eb380-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb380-113">備註</span><span class="sxs-lookup"><span data-stu-id="eb380-113">Remarks</span></span>  
 <span data-ttu-id="eb380-114">[Ihosttaskmanager:: Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)和[ihosttaskmanager:: Switchtotask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)這兩個方法會採用此類型的參數。</span><span class="sxs-lookup"><span data-stu-id="eb380-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb380-115">需求</span><span class="sxs-lookup"><span data-stu-id="eb380-115">Requirements</span></span>  
 <span data-ttu-id="eb380-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb380-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb380-117">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eb380-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb380-118">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb380-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb380-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb380-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb380-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb380-120">See Also</span></span>  
 [<span data-ttu-id="eb380-121">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="eb380-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
