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
ms.openlocfilehash: 0073a532f680d8764ec9e76ea22326a630457043
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176431"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="5baf7-102">EMemoryAvailable 列舉</span><span class="sxs-lookup"><span data-stu-id="5baf7-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="5baf7-103">包含指示電腦上可用實體記憶體量的值。</span><span class="sxs-lookup"><span data-stu-id="5baf7-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="5baf7-104">這些值以邏輯方式映射到 Windows API 中`CreateMemoryResourceNotification`函數返回的高記憶體和低記憶體的事件。</span><span class="sxs-lookup"><span data-stu-id="5baf7-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5baf7-105">語法</span><span class="sxs-lookup"><span data-stu-id="5baf7-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="5baf7-106">成員</span><span class="sxs-lookup"><span data-stu-id="5baf7-106">Members</span></span>  
  
|<span data-ttu-id="5baf7-107">member</span><span class="sxs-lookup"><span data-stu-id="5baf7-107">Member</span></span>|<span data-ttu-id="5baf7-108">描述</span><span class="sxs-lookup"><span data-stu-id="5baf7-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="5baf7-109">大量的實體記憶體可用。</span><span class="sxs-lookup"><span data-stu-id="5baf7-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="5baf7-110">幾乎沒有可用的實體記憶體。</span><span class="sxs-lookup"><span data-stu-id="5baf7-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="5baf7-111">可用的實體記憶體是中性的。</span><span class="sxs-lookup"><span data-stu-id="5baf7-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5baf7-112">備註</span><span class="sxs-lookup"><span data-stu-id="5baf7-112">Remarks</span></span>  
 <span data-ttu-id="5baf7-113">此值由主機傳遞到通用語言運行時 （CLR），方法是使用對[ICLR 記憶體通知回檔的調用：：在記憶體通知方法上](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)。</span><span class="sxs-lookup"><span data-stu-id="5baf7-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5baf7-114">需求</span><span class="sxs-lookup"><span data-stu-id="5baf7-114">Requirements</span></span>  
 <span data-ttu-id="5baf7-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5baf7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5baf7-116">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5baf7-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5baf7-117">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5baf7-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5baf7-118">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5baf7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5baf7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5baf7-119">See also</span></span>

- [<span data-ttu-id="5baf7-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="5baf7-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
