---
title: EMemoryAvailable 列舉
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0ffb85dc5f321e45432d6c2fa9448919957f0e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665197"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="8c081-102">EMemoryAvailable 列舉</span><span class="sxs-lookup"><span data-stu-id="8c081-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="8c081-103">包含值，表示電腦上的可用實體記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="8c081-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="8c081-104">這些值會以邏輯方式對應之事件記憶體從傳回的最高和最低`CreateMemoryResourceNotification`Win32 API 中的函式。</span><span class="sxs-lookup"><span data-stu-id="8c081-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Win32 API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c081-105">語法</span><span class="sxs-lookup"><span data-stu-id="8c081-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="8c081-106">成員</span><span class="sxs-lookup"><span data-stu-id="8c081-106">Members</span></span>  
  
|<span data-ttu-id="8c081-107">成員</span><span class="sxs-lookup"><span data-stu-id="8c081-107">Member</span></span>|<span data-ttu-id="8c081-108">描述</span><span class="sxs-lookup"><span data-stu-id="8c081-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="8c081-109">大量實體記憶體的使用。</span><span class="sxs-lookup"><span data-stu-id="8c081-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="8c081-110">使用極少的實體記憶體。</span><span class="sxs-lookup"><span data-stu-id="8c081-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="8c081-111">可用的實體記憶體不多不少。</span><span class="sxs-lookup"><span data-stu-id="8c081-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c081-112">備註</span><span class="sxs-lookup"><span data-stu-id="8c081-112">Remarks</span></span>  
 <span data-ttu-id="8c081-113">這個值會傳遞由 common language runtime (CLR) 主機所使用的呼叫來[iclrmemorynotificationcallback:: Onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="8c081-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c081-114">需求</span><span class="sxs-lookup"><span data-stu-id="8c081-114">Requirements</span></span>  
 <span data-ttu-id="8c081-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c081-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c081-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c081-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c081-117">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c081-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c081-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c081-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c081-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c081-119">See also</span></span>
- [<span data-ttu-id="8c081-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="8c081-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
