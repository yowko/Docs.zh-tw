---
title: EMemoryCriticalLevel 列舉
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
ms.openlocfilehash: 248f1d281697923e2da14517ca174fe615bba4ff
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616199"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="af0f2-102">EMemoryCriticalLevel 列舉</span><span class="sxs-lookup"><span data-stu-id="af0f2-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="af0f2-103">包含值，指出當要求特定記憶體配置但無法滿足時，失敗的影響。</span><span class="sxs-lookup"><span data-stu-id="af0f2-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af0f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="af0f2-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="af0f2-105">成員</span><span class="sxs-lookup"><span data-stu-id="af0f2-105">Members</span></span>  
  
|<span data-ttu-id="af0f2-106">成員</span><span class="sxs-lookup"><span data-stu-id="af0f2-106">Member</span></span>|<span data-ttu-id="af0f2-107">說明</span><span class="sxs-lookup"><span data-stu-id="af0f2-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="af0f2-108">表示在要求配置的網域中執行 managed 程式碼時，配置是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="af0f2-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="af0f2-109">如果無法配置記憶體，CLR 就無法保證該網域仍然可用。</span><span class="sxs-lookup"><span data-stu-id="af0f2-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="af0f2-110">主機會決定無法滿足配置時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="af0f2-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="af0f2-111">它可以指示 CLR `AppDomain` 自動中止，或藉由在[ICLRPolicyManager](iclrpolicymanager-interface.md)上呼叫方法，讓它繼續運作。</span><span class="sxs-lookup"><span data-stu-id="af0f2-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="af0f2-112">表示配置對於進程中的 managed 程式碼執行而言非常重要。</span><span class="sxs-lookup"><span data-stu-id="af0f2-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="af0f2-113">這個值會在啟動期間和執行完成項時使用。</span><span class="sxs-lookup"><span data-stu-id="af0f2-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="af0f2-114">如果無法配置記憶體，CLR 就無法在進程中運作。</span><span class="sxs-lookup"><span data-stu-id="af0f2-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="af0f2-115">如果配置失敗，CLR 會有效地停用。</span><span class="sxs-lookup"><span data-stu-id="af0f2-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="af0f2-116">所有對 CLR 的後續呼叫都會失敗，並 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="af0f2-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="af0f2-117">指出配置對於執行已要求配置的工作而言非常重要。</span><span class="sxs-lookup"><span data-stu-id="af0f2-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="af0f2-118">如果無法配置記憶體，CLR 就無法保證可以執行工作。</span><span class="sxs-lookup"><span data-stu-id="af0f2-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="af0f2-119">發生失敗時，CLR 會在 <xref:System.Threading.ThreadAbortException> 實體作業系統執行緒上引發。</span><span class="sxs-lookup"><span data-stu-id="af0f2-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af0f2-120">備註</span><span class="sxs-lookup"><span data-stu-id="af0f2-120">Remarks</span></span>  
 <span data-ttu-id="af0f2-121">[IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)和[IHostMAlloc](ihostmalloc-interface.md)介面中定義的記憶體配置方法會採用此類型的參數。</span><span class="sxs-lookup"><span data-stu-id="af0f2-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="af0f2-122">視失敗的嚴重性而定，主機可以決定是否要立即讓配置要求失敗，或等到它可以滿足為止。</span><span class="sxs-lookup"><span data-stu-id="af0f2-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af0f2-123">需求</span><span class="sxs-lookup"><span data-stu-id="af0f2-123">Requirements</span></span>  
 <span data-ttu-id="af0f2-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af0f2-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af0f2-125">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="af0f2-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af0f2-126">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="af0f2-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af0f2-127">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af0f2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af0f2-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af0f2-128">See also</span></span>

- [<span data-ttu-id="af0f2-129">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="af0f2-129">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="af0f2-130">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="af0f2-130">Hosting Enumerations</span></span>](hosting-enumerations.md)
