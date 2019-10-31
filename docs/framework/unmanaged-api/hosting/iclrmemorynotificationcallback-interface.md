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
ms.openlocfilehash: e980356ad592e137df7d08dadd77431b0e295380
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140998"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="fbcb2-102">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="fbcb2-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="fbcb2-103">可讓主機使用與 Win32 `CreateMemoryResourceNotification` 函式類似的方法來報告記憶體壓力狀況。</span><span class="sxs-lookup"><span data-stu-id="fbcb2-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fbcb2-104">方法</span><span class="sxs-lookup"><span data-stu-id="fbcb2-104">Methods</span></span>  
  
|<span data-ttu-id="fbcb2-105">方法</span><span class="sxs-lookup"><span data-stu-id="fbcb2-105">Method</span></span>|<span data-ttu-id="fbcb2-106">描述</span><span class="sxs-lookup"><span data-stu-id="fbcb2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fbcb2-107">OnMemoryNotification 方法</span><span class="sxs-lookup"><span data-stu-id="fbcb2-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="fbcb2-108">通知 common language runtime （CLR）電腦上的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="fbcb2-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbcb2-109">備註</span><span class="sxs-lookup"><span data-stu-id="fbcb2-109">Remarks</span></span>  
 <span data-ttu-id="fbcb2-110">主機會使用 `ICLRMemoryNotificationCallback` 介面來要求 CLR 釋放記憶體資源。</span><span class="sxs-lookup"><span data-stu-id="fbcb2-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbcb2-111">需求</span><span class="sxs-lookup"><span data-stu-id="fbcb2-111">Requirements</span></span>  
 <span data-ttu-id="fbcb2-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fbcb2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbcb2-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="fbcb2-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbcb2-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fbcb2-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbcb2-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbcb2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbcb2-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="fbcb2-116">See also</span></span>

- [<span data-ttu-id="fbcb2-117">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="fbcb2-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="fbcb2-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="fbcb2-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
