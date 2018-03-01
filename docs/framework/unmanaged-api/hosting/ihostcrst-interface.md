---
title: "IHostCrst 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3a9ed2b390ad741d90f9179ef5101d328d3b639d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="ba209-102">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="ba209-102">IHostCrst Interface</span></span>
<span data-ttu-id="ba209-103">可做為主機的關鍵區段的執行緒的表示法。</span><span class="sxs-lookup"><span data-stu-id="ba209-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba209-104">方法</span><span class="sxs-lookup"><span data-stu-id="ba209-104">Methods</span></span>  
  
|<span data-ttu-id="ba209-105">方法</span><span class="sxs-lookup"><span data-stu-id="ba209-105">Method</span></span>|<span data-ttu-id="ba209-106">描述</span><span class="sxs-lookup"><span data-stu-id="ba209-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba209-107">Enter 方法</span><span class="sxs-lookup"><span data-stu-id="ba209-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="ba209-108">進入重要區段。</span><span class="sxs-lookup"><span data-stu-id="ba209-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="ba209-109">Leave 方法</span><span class="sxs-lookup"><span data-stu-id="ba209-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="ba209-110">離開關鍵區段。</span><span class="sxs-lookup"><span data-stu-id="ba209-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="ba209-111">SetSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="ba209-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="ba209-112">設定關鍵區段的微調計數。</span><span class="sxs-lookup"><span data-stu-id="ba209-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="ba209-113">TryEnter 方法</span><span class="sxs-lookup"><span data-stu-id="ba209-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="ba209-114">嘗試立即進入重要區段，並報告成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="ba209-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba209-115">備註</span><span class="sxs-lookup"><span data-stu-id="ba209-115">Remarks</span></span>  
 <span data-ttu-id="ba209-116">`IHostCrst`可讓 common language runtime (CLR) 直接通訊的關鍵區段中，主機的表示法，而不是使用 Win32 函式，例如`EnterCriticalSection`或`LeaveCriticalSection`。</span><span class="sxs-lookup"><span data-stu-id="ba209-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba209-117">需求</span><span class="sxs-lookup"><span data-stu-id="ba209-117">Requirements</span></span>  
 <span data-ttu-id="ba209-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ba209-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba209-119">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ba209-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba209-120">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ba209-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba209-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba209-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba209-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="ba209-122">See Also</span></span>  
 [<span data-ttu-id="ba209-123">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="ba209-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="ba209-124">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="ba209-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="ba209-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="ba209-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
