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
ms.openlocfilehash: b3167d288a57575af85a9cb50f5c0cd82c8e9cc9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702791"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="2ca26-102">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="2ca26-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="2ca26-103">可讓主機使用的 Win32 類似的方法報告記憶體壓力狀況`CreateMemoryResourceNotification`函式。</span><span class="sxs-lookup"><span data-stu-id="2ca26-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2ca26-104">方法</span><span class="sxs-lookup"><span data-stu-id="2ca26-104">Methods</span></span>  
  
|<span data-ttu-id="2ca26-105">方法</span><span class="sxs-lookup"><span data-stu-id="2ca26-105">Method</span></span>|<span data-ttu-id="2ca26-106">描述</span><span class="sxs-lookup"><span data-stu-id="2ca26-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ca26-107">OnMemoryNotification 方法</span><span class="sxs-lookup"><span data-stu-id="2ca26-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="2ca26-108">在電腦上的記憶體負載會告知 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="2ca26-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ca26-109">備註</span><span class="sxs-lookup"><span data-stu-id="2ca26-109">Remarks</span></span>  
 <span data-ttu-id="2ca26-110">主機會使用`ICLRMemoryNotificationCallback`介面，以要求 CLR 釋放記憶體資源。</span><span class="sxs-lookup"><span data-stu-id="2ca26-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ca26-111">需求</span><span class="sxs-lookup"><span data-stu-id="2ca26-111">Requirements</span></span>  
 <span data-ttu-id="2ca26-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca26-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ca26-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ca26-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ca26-114">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2ca26-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ca26-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ca26-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca26-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ca26-116">See also</span></span>
- [<span data-ttu-id="2ca26-117">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="2ca26-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="2ca26-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="2ca26-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
