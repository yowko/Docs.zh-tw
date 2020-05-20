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
ms.openlocfilehash: 52fc21044d345998ad72c045cdf5e80a8a03a38e
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703810"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="6ca84-102">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6ca84-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="6ca84-103">可讓主機使用與 Win32 函數類似的方法來報告記憶體壓力狀況 `CreateMemoryResourceNotification` 。</span><span class="sxs-lookup"><span data-stu-id="6ca84-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ca84-104">方法</span><span class="sxs-lookup"><span data-stu-id="6ca84-104">Methods</span></span>  
  
|<span data-ttu-id="6ca84-105">方法</span><span class="sxs-lookup"><span data-stu-id="6ca84-105">Method</span></span>|<span data-ttu-id="6ca84-106">描述</span><span class="sxs-lookup"><span data-stu-id="6ca84-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ca84-107">OnMemoryNotification 方法</span><span class="sxs-lookup"><span data-stu-id="6ca84-107">OnMemoryNotification Method</span></span>](iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="6ca84-108">通知 common language runtime （CLR）電腦上的記憶體負載。</span><span class="sxs-lookup"><span data-stu-id="6ca84-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ca84-109">備註</span><span class="sxs-lookup"><span data-stu-id="6ca84-109">Remarks</span></span>  
 <span data-ttu-id="6ca84-110">主機 `ICLRMemoryNotificationCallback` 會使用介面來要求 CLR 可用記憶體資源。</span><span class="sxs-lookup"><span data-stu-id="6ca84-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ca84-111">需求</span><span class="sxs-lookup"><span data-stu-id="6ca84-111">Requirements</span></span>  
 <span data-ttu-id="6ca84-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ca84-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ca84-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="6ca84-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ca84-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6ca84-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ca84-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ca84-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca84-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ca84-116">See also</span></span>

- [<span data-ttu-id="6ca84-117">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="6ca84-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="6ca84-118">裝載介面</span><span class="sxs-lookup"><span data-stu-id="6ca84-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
