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
ms.openlocfilehash: 5762a354bec485cb382b5460dfd2a337f79bee1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689533"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="b6c3f-102">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b6c3f-102">ICLRMemoryNotificationCallback Interface</span></span>

<span data-ttu-id="b6c3f-103">允許主機使用類似 Win32 函數的方法來報告記憶體壓力條件 `CreateMemoryResourceNotification` 。</span><span class="sxs-lookup"><span data-stu-id="b6c3f-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6c3f-104">方法</span><span class="sxs-lookup"><span data-stu-id="b6c3f-104">Methods</span></span>  
  
|<span data-ttu-id="b6c3f-105">方法</span><span class="sxs-lookup"><span data-stu-id="b6c3f-105">Method</span></span>|<span data-ttu-id="b6c3f-106">描述</span><span class="sxs-lookup"><span data-stu-id="b6c3f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6c3f-107">OnMemoryNotification 方法</span><span class="sxs-lookup"><span data-stu-id="b6c3f-107">OnMemoryNotification Method</span></span>](iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="b6c3f-108">通知 common language runtime (CLR) 電腦上的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="b6c3f-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6c3f-109">備註</span><span class="sxs-lookup"><span data-stu-id="b6c3f-109">Remarks</span></span>  

 <span data-ttu-id="b6c3f-110">主機 `ICLRMemoryNotificationCallback` 會使用介面來要求 CLR 可用記憶體資源。</span><span class="sxs-lookup"><span data-stu-id="b6c3f-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6c3f-111">需求</span><span class="sxs-lookup"><span data-stu-id="b6c3f-111">Requirements</span></span>  

 <span data-ttu-id="b6c3f-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6c3f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6c3f-113">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b6c3f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6c3f-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="b6c3f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6c3f-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6c3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c3f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6c3f-116">See also</span></span>

- [<span data-ttu-id="b6c3f-117">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="b6c3f-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="b6c3f-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="b6c3f-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
