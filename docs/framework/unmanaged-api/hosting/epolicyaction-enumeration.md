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
ms.openlocfilehash: 901c62e6f2519fc4f9251f348c77b11bbe0992be
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504341"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="57b17-102">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="57b17-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="57b17-103">描述主機可以針對[EClrOperation](eclroperation-enumeration.md)所描述的作業設定的原則動作，以及[EClrFailure](eclrfailure-enumeration.md)所描述的失敗。</span><span class="sxs-lookup"><span data-stu-id="57b17-103">Describes the policy actions the host can set for operations described by [EClrOperation](eclroperation-enumeration.md) and failures described by [EClrFailure](eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57b17-104">語法</span><span class="sxs-lookup"><span data-stu-id="57b17-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="57b17-105">成員</span><span class="sxs-lookup"><span data-stu-id="57b17-105">Members</span></span>  
  
|<span data-ttu-id="57b17-106">成員</span><span class="sxs-lookup"><span data-stu-id="57b17-106">Member</span></span>|<span data-ttu-id="57b17-107">說明</span><span class="sxs-lookup"><span data-stu-id="57b17-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="57b17-108">指定 common language runtime （CLR）應正常中止執行緒。</span><span class="sxs-lookup"><span data-stu-id="57b17-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="57b17-109">「正常中止」包括嘗試執行所有 `finally` 區塊、與 `catch` 執行緒中止相關的任何區塊，以及完成項。</span><span class="sxs-lookup"><span data-stu-id="57b17-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="57b17-110">指定 CLR 應進入停用狀態。</span><span class="sxs-lookup"><span data-stu-id="57b17-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="57b17-111">在受影響的進程中無法執行進一步的 managed 程式碼，而且執行緒會遭到封鎖而無法進入 CLR。</span><span class="sxs-lookup"><span data-stu-id="57b17-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="57b17-112">指定 CLR 應該嘗試順利結束進程，包括執行完成項和執行清除和記錄作業。</span><span class="sxs-lookup"><span data-stu-id="57b17-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="57b17-113">指定 CLR 應該立即結束進程，而不執行完成項或清除和記錄作業。</span><span class="sxs-lookup"><span data-stu-id="57b17-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="57b17-114">不過，通知會傳送至偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="57b17-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="57b17-115">指定不採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="57b17-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="57b17-116">指定 CLR 應該執行強制執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="57b17-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="57b17-117">只有 `catch` 標示為 `finally` 的和區塊才 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 會執行。</span><span class="sxs-lookup"><span data-stu-id="57b17-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="57b17-118">指定 CLR 應該結束進程，而不執行完成項或記錄作業。</span><span class="sxs-lookup"><span data-stu-id="57b17-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="57b17-119">指定 CLR 應該執行的強制卸載 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="57b17-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="57b17-120">只會執行標記為的完成項 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="57b17-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="57b17-121">同樣地， <xref:System.AppDomain> 在其堆疊中的所有線程都會接收到 `ThreadAbortException` ，但 `catch` 只 `finally` 會執行標示為的那些和區塊 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="57b17-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="57b17-122">指定應該擲回條件適用的例外狀況，例如記憶體不足、緩衝區溢位等等。</span><span class="sxs-lookup"><span data-stu-id="57b17-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="57b17-123">指定應該卸載 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="57b17-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="57b17-124">CLR 嘗試執行完成項。</span><span class="sxs-lookup"><span data-stu-id="57b17-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57b17-125">備註</span><span class="sxs-lookup"><span data-stu-id="57b17-125">Remarks</span></span>  
 <span data-ttu-id="57b17-126">主機會藉由呼叫[ICLRPolicyManager](iclrpolicymanager-interface.md)介面的方法來設定原則動作。</span><span class="sxs-lookup"><span data-stu-id="57b17-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="57b17-127">如需有關強制性和正常中止的詳細資訊，請參閱[EClrOperation](eclroperation-enumeration.md)列舉。</span><span class="sxs-lookup"><span data-stu-id="57b17-127">For information about rude and graceful aborts, see the [EClrOperation](eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57b17-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="57b17-128">Requirements</span></span>  
 <span data-ttu-id="57b17-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57b17-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57b17-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="57b17-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57b17-131">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="57b17-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57b17-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57b17-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57b17-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57b17-133">See also</span></span>

- [<span data-ttu-id="57b17-134">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="57b17-134">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="57b17-135">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="57b17-135">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="57b17-136">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="57b17-136">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="57b17-137">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="57b17-137">Hosting Enumerations</span></span>](hosting-enumerations.md)
