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
ms.openlocfilehash: 6a8765bfd62a2e6543661804ab8d009ce19f8813
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724308"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="82aa3-102">EMemoryAvailable 列舉</span><span class="sxs-lookup"><span data-stu-id="82aa3-102">EMemoryAvailable Enumeration</span></span>

<span data-ttu-id="82aa3-103">包含值，指出電腦上可用的實體記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="82aa3-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="82aa3-104">這些值會以邏輯方式對應至 Windows API 中的函式所傳回之高和低記憶體的事件 `CreateMemoryResourceNotification` 。</span><span class="sxs-lookup"><span data-stu-id="82aa3-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82aa3-105">語法</span><span class="sxs-lookup"><span data-stu-id="82aa3-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="82aa3-106">成員</span><span class="sxs-lookup"><span data-stu-id="82aa3-106">Members</span></span>  
  
|<span data-ttu-id="82aa3-107">member</span><span class="sxs-lookup"><span data-stu-id="82aa3-107">Member</span></span>|<span data-ttu-id="82aa3-108">描述</span><span class="sxs-lookup"><span data-stu-id="82aa3-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="82aa3-109">有足夠的實體記憶體可供使用。</span><span class="sxs-lookup"><span data-stu-id="82aa3-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="82aa3-110">有極少的實體記憶體可用。</span><span class="sxs-lookup"><span data-stu-id="82aa3-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="82aa3-111">可用的實體記憶體是中立的。</span><span class="sxs-lookup"><span data-stu-id="82aa3-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82aa3-112">備註</span><span class="sxs-lookup"><span data-stu-id="82aa3-112">Remarks</span></span>  

 <span data-ttu-id="82aa3-113">使用 [ICLRMemoryNotificationCallback：： OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) 方法的呼叫，此值會由主機傳遞給 common language RUNTIME (CLR) 。</span><span class="sxs-lookup"><span data-stu-id="82aa3-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82aa3-114">需求</span><span class="sxs-lookup"><span data-stu-id="82aa3-114">Requirements</span></span>  

 <span data-ttu-id="82aa3-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82aa3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82aa3-116">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="82aa3-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82aa3-117">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82aa3-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82aa3-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82aa3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82aa3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82aa3-119">See also</span></span>

- [<span data-ttu-id="82aa3-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="82aa3-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
