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
ms.openlocfilehash: e8cb1486ccea11ba6edcf7bbb781a9bf210b496d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804908"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="1e537-102">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="1e537-102">IHostCrst Interface</span></span>
<span data-ttu-id="1e537-103">作為執行緒之重要區段的主機標記法。</span><span class="sxs-lookup"><span data-stu-id="1e537-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e537-104">方法</span><span class="sxs-lookup"><span data-stu-id="1e537-104">Methods</span></span>  
  
|<span data-ttu-id="1e537-105">方法</span><span class="sxs-lookup"><span data-stu-id="1e537-105">Method</span></span>|<span data-ttu-id="1e537-106">描述</span><span class="sxs-lookup"><span data-stu-id="1e537-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e537-107">Enter 方法</span><span class="sxs-lookup"><span data-stu-id="1e537-107">Enter Method</span></span>](ihostcrst-enter-method.md)|<span data-ttu-id="1e537-108">進入重要區段。</span><span class="sxs-lookup"><span data-stu-id="1e537-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="1e537-109">Leave 方法</span><span class="sxs-lookup"><span data-stu-id="1e537-109">Leave Method</span></span>](ihostcrst-leave-method.md)|<span data-ttu-id="1e537-110">離開重要區段。</span><span class="sxs-lookup"><span data-stu-id="1e537-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="1e537-111">SetSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="1e537-111">SetSpinCount Method</span></span>](ihostcrst-setspincount-method.md)|<span data-ttu-id="1e537-112">設定重要區段的微調計數。</span><span class="sxs-lookup"><span data-stu-id="1e537-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="1e537-113">TryEnter 方法</span><span class="sxs-lookup"><span data-stu-id="1e537-113">TryEnter Method</span></span>](ihostcrst-tryenter-method.md)|<span data-ttu-id="1e537-114">嘗試進入重要區段，並立即報告成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="1e537-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e537-115">備註</span><span class="sxs-lookup"><span data-stu-id="1e537-115">Remarks</span></span>  
 <span data-ttu-id="1e537-116">`IHostCrst`允許 common language runtime （CLR）直接與主控制項的重要區段表示進行通訊，而不是使用 Win32 函數，例如 `EnterCriticalSection` 或 `LeaveCriticalSection` 。</span><span class="sxs-lookup"><span data-stu-id="1e537-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e537-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="1e537-117">Requirements</span></span>  
 <span data-ttu-id="1e537-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e537-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e537-119">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="1e537-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e537-120">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1e537-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e537-121">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e537-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e537-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e537-122">See also</span></span>

- [<span data-ttu-id="1e537-123">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="1e537-123">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="1e537-124">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="1e537-124">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="1e537-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="1e537-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
