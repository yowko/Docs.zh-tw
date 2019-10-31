---
title: EPolicyAction 列舉
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
ms.openlocfilehash: eaba6b2166a82cfe825ffb98db515e24d4656462
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138237"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="dffdf-102">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="dffdf-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="dffdf-103">描述主機可以針對[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)所描述的作業設定的原則動作，以及[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)所描述的失敗。</span><span class="sxs-lookup"><span data-stu-id="dffdf-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dffdf-104">語法</span><span class="sxs-lookup"><span data-stu-id="dffdf-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a><span data-ttu-id="dffdf-105">Members</span><span class="sxs-lookup"><span data-stu-id="dffdf-105">Members</span></span>  
  
|<span data-ttu-id="dffdf-106">成員</span><span class="sxs-lookup"><span data-stu-id="dffdf-106">Member</span></span>|<span data-ttu-id="dffdf-107">描述</span><span class="sxs-lookup"><span data-stu-id="dffdf-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="dffdf-108">指定 common language runtime （CLR）應正常中止執行緒。</span><span class="sxs-lookup"><span data-stu-id="dffdf-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="dffdf-109">「正常中止」包括嘗試執行所有 `finally` 區塊、與執行緒中止相關的任何 `catch` 區塊，以及完成項。</span><span class="sxs-lookup"><span data-stu-id="dffdf-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="dffdf-110">指定 CLR 應進入停用狀態。</span><span class="sxs-lookup"><span data-stu-id="dffdf-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="dffdf-111">在受影響的進程中無法執行進一步的 managed 程式碼，而且執行緒會遭到封鎖而無法進入 CLR。</span><span class="sxs-lookup"><span data-stu-id="dffdf-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="dffdf-112">指定 CLR 應該嘗試順利結束進程，包括執行完成項和執行清除和記錄作業。</span><span class="sxs-lookup"><span data-stu-id="dffdf-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="dffdf-113">指定 CLR 應該立即結束進程，而不執行完成項或清除和記錄作業。</span><span class="sxs-lookup"><span data-stu-id="dffdf-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="dffdf-114">不過，通知會傳送至偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="dffdf-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="dffdf-115">指定不採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="dffdf-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="dffdf-116">指定 CLR 應該執行強制執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="dffdf-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="dffdf-117">只有標示 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 的 `catch` 和 `finally` 區塊才會執行。</span><span class="sxs-lookup"><span data-stu-id="dffdf-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="dffdf-118">指定 CLR 應該結束進程，而不執行完成項或記錄作業。</span><span class="sxs-lookup"><span data-stu-id="dffdf-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="dffdf-119">指定 CLR 應該執行 <xref:System.AppDomain>的強制卸載。</span><span class="sxs-lookup"><span data-stu-id="dffdf-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="dffdf-120">只會執行標示為 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 的完成項。</span><span class="sxs-lookup"><span data-stu-id="dffdf-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="dffdf-121">同樣地，此 <xref:System.AppDomain> 在其堆疊中的所有線程都會收到 `ThreadAbortException`，但只會執行標示為 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 的 `catch` 和 `finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="dffdf-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="dffdf-122">指定應該擲回條件適用的例外狀況，例如記憶體不足、緩衝區溢位等等。</span><span class="sxs-lookup"><span data-stu-id="dffdf-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="dffdf-123">指定應該卸載 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="dffdf-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="dffdf-124">CLR 嘗試執行完成項。</span><span class="sxs-lookup"><span data-stu-id="dffdf-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dffdf-125">備註</span><span class="sxs-lookup"><span data-stu-id="dffdf-125">Remarks</span></span>  
 <span data-ttu-id="dffdf-126">主機會藉由呼叫[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)介面的方法來設定原則動作。</span><span class="sxs-lookup"><span data-stu-id="dffdf-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="dffdf-127">如需有關強制性和正常中止的詳細資訊，請參閱[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)列舉。</span><span class="sxs-lookup"><span data-stu-id="dffdf-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dffdf-128">需求</span><span class="sxs-lookup"><span data-stu-id="dffdf-128">Requirements</span></span>  
 <span data-ttu-id="dffdf-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dffdf-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dffdf-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="dffdf-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dffdf-131">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="dffdf-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dffdf-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dffdf-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffdf-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="dffdf-133">See also</span></span>

- [<span data-ttu-id="dffdf-134">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="dffdf-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="dffdf-135">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="dffdf-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="dffdf-136">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="dffdf-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="dffdf-137">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="dffdf-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
