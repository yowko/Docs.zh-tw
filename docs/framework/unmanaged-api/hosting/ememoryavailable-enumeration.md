---
title: "EMemoryAvailable 列舉"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 596b174fa4ebac7e54e2f6b5f3ed044686fa515f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="b5a44-102">EMemoryAvailable 列舉</span><span class="sxs-lookup"><span data-stu-id="b5a44-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="b5a44-103">包含值，表示電腦上的可用實體記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="b5a44-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="b5a44-104">這些值以邏輯方式對應至事件的記憶體從傳回的最高和最低`CreateMemoryResourceNotification`Win32 API 中的函式。</span><span class="sxs-lookup"><span data-stu-id="b5a44-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Win32 API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5a44-105">語法</span><span class="sxs-lookup"><span data-stu-id="b5a44-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="b5a44-106">成員</span><span class="sxs-lookup"><span data-stu-id="b5a44-106">Members</span></span>  
  
|<span data-ttu-id="b5a44-107">成員</span><span class="sxs-lookup"><span data-stu-id="b5a44-107">Member</span></span>|<span data-ttu-id="b5a44-108">描述</span><span class="sxs-lookup"><span data-stu-id="b5a44-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="b5a44-109">足夠的實體記憶體使用。</span><span class="sxs-lookup"><span data-stu-id="b5a44-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="b5a44-110">使用實體記憶體很少。</span><span class="sxs-lookup"><span data-stu-id="b5a44-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="b5a44-111">可用的實體記憶體是中性。</span><span class="sxs-lookup"><span data-stu-id="b5a44-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5a44-112">備註</span><span class="sxs-lookup"><span data-stu-id="b5a44-112">Remarks</span></span>  
 <span data-ttu-id="b5a44-113">這個值會傳遞由 common language runtime (CLR) 主機所使用的呼叫[iclrmemorynotificationcallback:: Onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b5a44-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5a44-114">需求</span><span class="sxs-lookup"><span data-stu-id="b5a44-114">Requirements</span></span>  
 <span data-ttu-id="b5a44-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5a44-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5a44-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b5a44-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5a44-117">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5a44-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5a44-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5a44-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a44-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5a44-119">See Also</span></span>  
 [<span data-ttu-id="b5a44-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="b5a44-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
