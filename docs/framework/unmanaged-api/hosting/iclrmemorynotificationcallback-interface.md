---
title: "ICLRMemoryNotificationCallback 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMemoryNotificationCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMemoryNotificationCallback
helpviewer_keywords: ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b998f8af2c7f4add3ecbb905928b5956409bf00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="9797a-102">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9797a-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="9797a-103">可讓主機使用的方法類似的 Win32 報表記憶體壓力狀況`CreateMemoryResourceNotification`函式。</span><span class="sxs-lookup"><span data-stu-id="9797a-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9797a-104">方法</span><span class="sxs-lookup"><span data-stu-id="9797a-104">Methods</span></span>  
  
|<span data-ttu-id="9797a-105">方法</span><span class="sxs-lookup"><span data-stu-id="9797a-105">Method</span></span>|<span data-ttu-id="9797a-106">說明</span><span class="sxs-lookup"><span data-stu-id="9797a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9797a-107">OnMemoryNotification 方法</span><span class="sxs-lookup"><span data-stu-id="9797a-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="9797a-108">通知 common language runtime (CLR) 的電腦上的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="9797a-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9797a-109">備註</span><span class="sxs-lookup"><span data-stu-id="9797a-109">Remarks</span></span>  
 <span data-ttu-id="9797a-110">主機會使用`ICLRMemoryNotificationCallback`要求 CLR 釋放記憶體資源的介面。</span><span class="sxs-lookup"><span data-stu-id="9797a-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9797a-111">需求</span><span class="sxs-lookup"><span data-stu-id="9797a-111">Requirements</span></span>  
 <span data-ttu-id="9797a-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9797a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9797a-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9797a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9797a-114">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9797a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9797a-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9797a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9797a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9797a-116">See Also</span></span>  
 [<span data-ttu-id="9797a-117">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="9797a-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="9797a-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9797a-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
