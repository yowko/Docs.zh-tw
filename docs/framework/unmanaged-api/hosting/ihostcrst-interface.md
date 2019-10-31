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
ms.openlocfilehash: 108492ba298e9f8429b2acd890ab3404365bc602
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130517"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="725a9-102">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="725a9-102">IHostCrst Interface</span></span>
<span data-ttu-id="725a9-103">作為執行緒之重要區段的主機標記法。</span><span class="sxs-lookup"><span data-stu-id="725a9-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="725a9-104">方法</span><span class="sxs-lookup"><span data-stu-id="725a9-104">Methods</span></span>  
  
|<span data-ttu-id="725a9-105">方法</span><span class="sxs-lookup"><span data-stu-id="725a9-105">Method</span></span>|<span data-ttu-id="725a9-106">描述</span><span class="sxs-lookup"><span data-stu-id="725a9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="725a9-107">Enter 方法</span><span class="sxs-lookup"><span data-stu-id="725a9-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="725a9-108">進入重要區段。</span><span class="sxs-lookup"><span data-stu-id="725a9-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="725a9-109">Leave 方法</span><span class="sxs-lookup"><span data-stu-id="725a9-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="725a9-110">離開重要區段。</span><span class="sxs-lookup"><span data-stu-id="725a9-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="725a9-111">SetSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="725a9-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="725a9-112">設定重要區段的微調計數。</span><span class="sxs-lookup"><span data-stu-id="725a9-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="725a9-113">TryEnter 方法</span><span class="sxs-lookup"><span data-stu-id="725a9-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="725a9-114">嘗試進入重要區段，並立即報告成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="725a9-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="725a9-115">備註</span><span class="sxs-lookup"><span data-stu-id="725a9-115">Remarks</span></span>  
 <span data-ttu-id="725a9-116">`IHostCrst` 可讓 common language runtime （CLR）直接與主控制項的重要區段表示進行通訊，而不是使用 `EnterCriticalSection` 或 `LeaveCriticalSection`之類的 Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="725a9-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="725a9-117">需求</span><span class="sxs-lookup"><span data-stu-id="725a9-117">Requirements</span></span>  
 <span data-ttu-id="725a9-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="725a9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="725a9-119">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="725a9-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="725a9-120">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="725a9-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="725a9-121">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="725a9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725a9-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="725a9-122">See also</span></span>

- [<span data-ttu-id="725a9-123">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="725a9-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="725a9-124">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="725a9-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="725a9-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="725a9-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
