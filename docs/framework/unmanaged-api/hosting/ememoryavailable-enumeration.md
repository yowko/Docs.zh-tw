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
ms.openlocfilehash: aec3c5f140df7eab10ea2bfa33634a4d853adcb0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134295"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="04a61-102">EMemoryAvailable 列舉</span><span class="sxs-lookup"><span data-stu-id="04a61-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="04a61-103">包含值，指出電腦上的可用實體記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="04a61-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="04a61-104">這些值會以邏輯方式對應至 Windows API 中 `CreateMemoryResourceNotification` 函式所傳回之高和低記憶體的事件。</span><span class="sxs-lookup"><span data-stu-id="04a61-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a61-105">語法</span><span class="sxs-lookup"><span data-stu-id="04a61-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="04a61-106">Members</span><span class="sxs-lookup"><span data-stu-id="04a61-106">Members</span></span>  
  
|<span data-ttu-id="04a61-107">成員</span><span class="sxs-lookup"><span data-stu-id="04a61-107">Member</span></span>|<span data-ttu-id="04a61-108">描述</span><span class="sxs-lookup"><span data-stu-id="04a61-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="04a61-109">有足夠的實體記憶體可供使用。</span><span class="sxs-lookup"><span data-stu-id="04a61-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="04a61-110">有極少的實體記憶體可供使用。</span><span class="sxs-lookup"><span data-stu-id="04a61-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="04a61-111">可用的實體記憶體是中性的。</span><span class="sxs-lookup"><span data-stu-id="04a61-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04a61-112">備註</span><span class="sxs-lookup"><span data-stu-id="04a61-112">Remarks</span></span>  
 <span data-ttu-id="04a61-113">此值會透過呼叫[ICLRMemoryNotificationCallback：： OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)方法，由主機傳遞至 common language RUNTIME （CLR）。</span><span class="sxs-lookup"><span data-stu-id="04a61-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04a61-114">需求</span><span class="sxs-lookup"><span data-stu-id="04a61-114">Requirements</span></span>  
 <span data-ttu-id="04a61-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04a61-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04a61-116">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="04a61-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04a61-117">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="04a61-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04a61-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04a61-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a61-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="04a61-119">See also</span></span>

- [<span data-ttu-id="04a61-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="04a61-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
