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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26b3761ab49f36c5f687ff2c62882667e044d299
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774225"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="edc67-102">EMemoryCriticalLevel 列舉</span><span class="sxs-lookup"><span data-stu-id="edc67-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="edc67-103">包含值，表示失敗的影響，當有特定記憶體配置已要求但不能滿足。</span><span class="sxs-lookup"><span data-stu-id="edc67-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edc67-104">語法</span><span class="sxs-lookup"><span data-stu-id="edc67-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="edc67-105">成員</span><span class="sxs-lookup"><span data-stu-id="edc67-105">Members</span></span>  
  
|<span data-ttu-id="edc67-106">成員</span><span class="sxs-lookup"><span data-stu-id="edc67-106">Member</span></span>|<span data-ttu-id="edc67-107">說明</span><span class="sxs-lookup"><span data-stu-id="edc67-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="edc67-108">指出配置已要求配置的網域中執行 managed 程式碼的重要。</span><span class="sxs-lookup"><span data-stu-id="edc67-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="edc67-109">如果無法配置記憶體，CLR 不保證仍可使用定義域。</span><span class="sxs-lookup"><span data-stu-id="edc67-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="edc67-110">主應用程式會決定當無法滿足配置時要採取什麼動作。</span><span class="sxs-lookup"><span data-stu-id="edc67-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="edc67-111">它可以指示 CLR 在中止`AppDomain`自動執行，或允許它繼續執行上呼叫方法[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="edc67-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="edc67-112">指出配置重要的程序中的 managed 程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="edc67-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="edc67-113">這個值可在啟動期間，當執行完成項。</span><span class="sxs-lookup"><span data-stu-id="edc67-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="edc67-114">如果無法配置記憶體，CLR 無法在程序。</span><span class="sxs-lookup"><span data-stu-id="edc67-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="edc67-115">如果配置失敗，CLR 會有效地停用。</span><span class="sxs-lookup"><span data-stu-id="edc67-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="edc67-116">所有後續的呼叫，clr 會失敗並 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="edc67-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="edc67-117">表示配置務必執行之工作的要求配置。</span><span class="sxs-lookup"><span data-stu-id="edc67-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="edc67-118">如果無法配置記憶體，CLR 不保證可以執行此工作。</span><span class="sxs-lookup"><span data-stu-id="edc67-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="edc67-119">如果發生失敗，CLR 會引發<xref:System.Threading.ThreadAbortException>實體作業系統執行緒上。</span><span class="sxs-lookup"><span data-stu-id="edc67-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edc67-120">備註</span><span class="sxs-lookup"><span data-stu-id="edc67-120">Remarks</span></span>  
 <span data-ttu-id="edc67-121">中所定義的記憶體配置方法[IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)並[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)介面採用這種類型的參數。</span><span class="sxs-lookup"><span data-stu-id="edc67-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="edc67-122">失敗的嚴重性而定，主機可以決定是否要立即拒絕配置要求，或等候，直到可以滿足。</span><span class="sxs-lookup"><span data-stu-id="edc67-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edc67-123">需求</span><span class="sxs-lookup"><span data-stu-id="edc67-123">Requirements</span></span>  
 <span data-ttu-id="edc67-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="edc67-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edc67-125">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="edc67-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="edc67-126">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="edc67-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="edc67-127">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edc67-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edc67-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edc67-128">See also</span></span>

- [<span data-ttu-id="edc67-129">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="edc67-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="edc67-130">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="edc67-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
