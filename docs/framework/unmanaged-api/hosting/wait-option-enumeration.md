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
ms.openlocfilehash: 9ecfb551b55551e5f6cc7e7e9ffb55e5a96259ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141510"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="4103e-102">WAIT_OPTION 列舉</span><span class="sxs-lookup"><span data-stu-id="4103e-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="4103e-103">包含值，指出當 common language runtime （CLR）區塊要求的作業時，主機應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="4103e-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4103e-104">語法</span><span class="sxs-lookup"><span data-stu-id="4103e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="4103e-105">Members</span><span class="sxs-lookup"><span data-stu-id="4103e-105">Members</span></span>  
  
|<span data-ttu-id="4103e-106">成員</span><span class="sxs-lookup"><span data-stu-id="4103e-106">Member</span></span>|<span data-ttu-id="4103e-107">描述</span><span class="sxs-lookup"><span data-stu-id="4103e-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="4103e-108">當 CLR 呼叫[IHostTask：： Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)方法時，通知主機應該喚醒工作。</span><span class="sxs-lookup"><span data-stu-id="4103e-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="4103e-109">當執行緒遭到封鎖時，通知主機必須在目前的 OS 執行緒上提取訊息。</span><span class="sxs-lookup"><span data-stu-id="4103e-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="4103e-110">執行時間只會在 <xref:System.Threading.ApartmentState.STA> 執行緒上指定此值。</span><span class="sxs-lookup"><span data-stu-id="4103e-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="4103e-111">通知主機，主機無法中斷指定的同步處理要求。</span><span class="sxs-lookup"><span data-stu-id="4103e-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="4103e-112">也就是，主機無法傳回 `HOST_E_DEADLOCK`。</span><span class="sxs-lookup"><span data-stu-id="4103e-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4103e-113">備註</span><span class="sxs-lookup"><span data-stu-id="4103e-113">Remarks</span></span>  
 <span data-ttu-id="4103e-114">[IHostTaskManager：： Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)和[IHostTaskManager：： SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)方法都採用此類型的參數。</span><span class="sxs-lookup"><span data-stu-id="4103e-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4103e-115">需求</span><span class="sxs-lookup"><span data-stu-id="4103e-115">Requirements</span></span>  
 <span data-ttu-id="4103e-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4103e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4103e-117">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="4103e-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4103e-118">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="4103e-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4103e-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4103e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4103e-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="4103e-120">See also</span></span>

- [<span data-ttu-id="4103e-121">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="4103e-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
