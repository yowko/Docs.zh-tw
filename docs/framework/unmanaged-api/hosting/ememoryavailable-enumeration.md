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
ms.openlocfilehash: 76fc5f578e6da731ffd6406344d00cda8b57f493
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772403"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="fcdaa-102">EMemoryAvailable 列舉</span><span class="sxs-lookup"><span data-stu-id="fcdaa-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="fcdaa-103">包含值，表示電腦上的可用實體記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="fcdaa-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="fcdaa-104">這些值會以邏輯方式對應之事件記憶體從傳回的最高和最低`CreateMemoryResourceNotification`Windows API 中的函式。</span><span class="sxs-lookup"><span data-stu-id="fcdaa-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcdaa-105">語法</span><span class="sxs-lookup"><span data-stu-id="fcdaa-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="fcdaa-106">成員</span><span class="sxs-lookup"><span data-stu-id="fcdaa-106">Members</span></span>  
  
|<span data-ttu-id="fcdaa-107">成員</span><span class="sxs-lookup"><span data-stu-id="fcdaa-107">Member</span></span>|<span data-ttu-id="fcdaa-108">描述</span><span class="sxs-lookup"><span data-stu-id="fcdaa-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="fcdaa-109">大量實體記憶體的使用。</span><span class="sxs-lookup"><span data-stu-id="fcdaa-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="fcdaa-110">使用極少的實體記憶體。</span><span class="sxs-lookup"><span data-stu-id="fcdaa-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="fcdaa-111">可用的實體記憶體不多不少。</span><span class="sxs-lookup"><span data-stu-id="fcdaa-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcdaa-112">備註</span><span class="sxs-lookup"><span data-stu-id="fcdaa-112">Remarks</span></span>  
 <span data-ttu-id="fcdaa-113">這個值會傳遞由 common language runtime (CLR) 主機所使用的呼叫來[iclrmemorynotificationcallback:: Onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="fcdaa-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcdaa-114">需求</span><span class="sxs-lookup"><span data-stu-id="fcdaa-114">Requirements</span></span>  
 <span data-ttu-id="fcdaa-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fcdaa-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcdaa-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fcdaa-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fcdaa-117">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fcdaa-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fcdaa-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcdaa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcdaa-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcdaa-119">See also</span></span>

- [<span data-ttu-id="fcdaa-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="fcdaa-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
