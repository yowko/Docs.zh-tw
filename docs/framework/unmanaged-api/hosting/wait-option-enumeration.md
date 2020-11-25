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
ms.openlocfilehash: 056d41df328de5796eec9f04589205d18b408f1f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732797"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="0eae5-102">WAIT_OPTION 列舉</span><span class="sxs-lookup"><span data-stu-id="0eae5-102">WAIT_OPTION Enumeration</span></span>

<span data-ttu-id="0eae5-103">包含值，這些值會指出 common language runtime (CLR) 區塊所要求的作業時，主機所應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="0eae5-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eae5-104">語法</span><span class="sxs-lookup"><span data-stu-id="0eae5-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="0eae5-105">成員</span><span class="sxs-lookup"><span data-stu-id="0eae5-105">Members</span></span>  
  
|<span data-ttu-id="0eae5-106">member</span><span class="sxs-lookup"><span data-stu-id="0eae5-106">Member</span></span>|<span data-ttu-id="0eae5-107">描述</span><span class="sxs-lookup"><span data-stu-id="0eae5-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="0eae5-108">通知主機，如果 CLR 呼叫 [IHostTask：： Alert](ihosttask-alert-method.md) 方法，則應該喚醒工作。</span><span class="sxs-lookup"><span data-stu-id="0eae5-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="0eae5-109">通知主機必須線上程遭到封鎖時，在目前的 OS 執行緒上提取訊息。</span><span class="sxs-lookup"><span data-stu-id="0eae5-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="0eae5-110">執行時間只會線上程上指定此值 <xref:System.Threading.ApartmentState.STA> 。</span><span class="sxs-lookup"><span data-stu-id="0eae5-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="0eae5-111">通知主機，主機無法中斷指定的同步處理要求。</span><span class="sxs-lookup"><span data-stu-id="0eae5-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="0eae5-112">也就是說，主機無法返回 `HOST_E_DEADLOCK` 。</span><span class="sxs-lookup"><span data-stu-id="0eae5-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eae5-113">備註</span><span class="sxs-lookup"><span data-stu-id="0eae5-113">Remarks</span></span>  

 <span data-ttu-id="0eae5-114">[IHostTaskManager：： Sleep](ihosttaskmanager-sleep-method.md)和[IHostTaskManager：： SwitchToTask](ihosttaskmanager-switchtotask-method.md)方法都採用此類型的參數。</span><span class="sxs-lookup"><span data-stu-id="0eae5-114">The [IHostTaskManager::Sleep](ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eae5-115">需求</span><span class="sxs-lookup"><span data-stu-id="0eae5-115">Requirements</span></span>  

 <span data-ttu-id="0eae5-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0eae5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eae5-117">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0eae5-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0eae5-118">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0eae5-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0eae5-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eae5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eae5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0eae5-120">See also</span></span>

- [<span data-ttu-id="0eae5-121">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="0eae5-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
