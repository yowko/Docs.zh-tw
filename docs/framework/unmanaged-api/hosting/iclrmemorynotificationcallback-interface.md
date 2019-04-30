---
title: ICLRMemoryNotificationCallback 介面
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c98ece9d60571034f3298f15897b10c4d8fb06f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948547"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="6b35f-102">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6b35f-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="6b35f-103">可讓主機使用的 Win32 類似的方法報告記憶體壓力狀況`CreateMemoryResourceNotification`函式。</span><span class="sxs-lookup"><span data-stu-id="6b35f-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6b35f-104">方法</span><span class="sxs-lookup"><span data-stu-id="6b35f-104">Methods</span></span>  
  
|<span data-ttu-id="6b35f-105">方法</span><span class="sxs-lookup"><span data-stu-id="6b35f-105">Method</span></span>|<span data-ttu-id="6b35f-106">描述</span><span class="sxs-lookup"><span data-stu-id="6b35f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6b35f-107">OnMemoryNotification 方法</span><span class="sxs-lookup"><span data-stu-id="6b35f-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="6b35f-108">在電腦上的記憶體負載會告知 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="6b35f-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b35f-109">備註</span><span class="sxs-lookup"><span data-stu-id="6b35f-109">Remarks</span></span>  
 <span data-ttu-id="6b35f-110">主機會使用`ICLRMemoryNotificationCallback`介面，以要求 CLR 釋放記憶體資源。</span><span class="sxs-lookup"><span data-stu-id="6b35f-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b35f-111">需求</span><span class="sxs-lookup"><span data-stu-id="6b35f-111">Requirements</span></span>  
 <span data-ttu-id="6b35f-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b35f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b35f-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b35f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b35f-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6b35f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b35f-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b35f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b35f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b35f-116">See also</span></span>

- [<span data-ttu-id="6b35f-117">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="6b35f-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="6b35f-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="6b35f-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
