---
title: IHostCrst 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 939f100e8ee386642a29c33827a8339caf0467b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193183"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="e85fd-102">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="e85fd-102">IHostCrst Interface</span></span>
<span data-ttu-id="e85fd-103">可做為執行緒的關鍵區段之主機的表示法。</span><span class="sxs-lookup"><span data-stu-id="e85fd-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e85fd-104">方法</span><span class="sxs-lookup"><span data-stu-id="e85fd-104">Methods</span></span>  
  
|<span data-ttu-id="e85fd-105">方法</span><span class="sxs-lookup"><span data-stu-id="e85fd-105">Method</span></span>|<span data-ttu-id="e85fd-106">描述</span><span class="sxs-lookup"><span data-stu-id="e85fd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e85fd-107">Enter 方法</span><span class="sxs-lookup"><span data-stu-id="e85fd-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="e85fd-108">進入重要區段。</span><span class="sxs-lookup"><span data-stu-id="e85fd-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="e85fd-109">Leave 方法</span><span class="sxs-lookup"><span data-stu-id="e85fd-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="e85fd-110">離開重要區段。</span><span class="sxs-lookup"><span data-stu-id="e85fd-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="e85fd-111">SetSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="e85fd-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="e85fd-112">設定為關鍵區段旋轉計數。</span><span class="sxs-lookup"><span data-stu-id="e85fd-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="e85fd-113">TryEnter 方法</span><span class="sxs-lookup"><span data-stu-id="e85fd-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="e85fd-114">嘗試立即進入重要區段，並報告成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="e85fd-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e85fd-115">備註</span><span class="sxs-lookup"><span data-stu-id="e85fd-115">Remarks</span></span>  
 `IHostCrst` <span data-ttu-id="e85fd-116">可讓 common language runtime (CLR) 直接通訊的重要區段中，主機的表示法，而不是使用 Win32 函式，例如`EnterCriticalSection`或`LeaveCriticalSection`。</span><span class="sxs-lookup"><span data-stu-id="e85fd-116">allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e85fd-117">需求</span><span class="sxs-lookup"><span data-stu-id="e85fd-117">Requirements</span></span>  
 <span data-ttu-id="e85fd-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e85fd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e85fd-119">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e85fd-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e85fd-120">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e85fd-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e85fd-121">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e85fd-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e85fd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e85fd-122">See also</span></span>

- [<span data-ttu-id="e85fd-123">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="e85fd-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e85fd-124">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="e85fd-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="e85fd-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="e85fd-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
