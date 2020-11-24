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
ms.openlocfilehash: 72b371d72b2f055f2840da5595d9022ffd7e2507
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674726"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="33122-102">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="33122-102">EPolicyAction Enumeration</span></span>

<span data-ttu-id="33122-103">描述主機可針對 [EClrOperation](eclroperation-enumeration.md) 所描述的作業所設定的原則動作，以及 [EClrFailure](eclrfailure-enumeration.md)所描述的失敗。</span><span class="sxs-lookup"><span data-stu-id="33122-103">Describes the policy actions the host can set for operations described by [EClrOperation](eclroperation-enumeration.md) and failures described by [EClrFailure](eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33122-104">語法</span><span class="sxs-lookup"><span data-stu-id="33122-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="33122-105">成員</span><span class="sxs-lookup"><span data-stu-id="33122-105">Members</span></span>  
  
|<span data-ttu-id="33122-106">member</span><span class="sxs-lookup"><span data-stu-id="33122-106">Member</span></span>|<span data-ttu-id="33122-107">描述</span><span class="sxs-lookup"><span data-stu-id="33122-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="33122-108">指定 common language runtime (CLR) 應正常中止執行緒。</span><span class="sxs-lookup"><span data-stu-id="33122-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="33122-109">正常中止包括嘗試執行所有 `finally` 區塊、與 `catch` 執行緒中止相關的任何區塊，以及完成項。</span><span class="sxs-lookup"><span data-stu-id="33122-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="33122-110">指定 CLR 應進入停用狀態。</span><span class="sxs-lookup"><span data-stu-id="33122-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="33122-111">無法在受影響的進程中執行任何進一步的 managed 程式碼，且會封鎖執行緒進入 CLR。</span><span class="sxs-lookup"><span data-stu-id="33122-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="33122-112">指定 CLR 應嘗試正常結束進程，包括執行完成項和執行清除和記錄作業。</span><span class="sxs-lookup"><span data-stu-id="33122-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="33122-113">指定 CLR 應該立即結束進程，而不執行完成項或執行清除和記錄作業。</span><span class="sxs-lookup"><span data-stu-id="33122-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="33122-114">不過，通知會傳送至偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="33122-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="33122-115">指定不採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="33122-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="33122-116">指定 CLR 應該執行強制執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="33122-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="33122-117">只 `catch` `finally` 會執行標示為的和區塊 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="33122-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="33122-118">指定 CLR 應結束進程，而不執行完成項或記錄作業。</span><span class="sxs-lookup"><span data-stu-id="33122-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="33122-119">指定 CLR 應該執行的強制卸載 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="33122-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="33122-120">只會執行標示為的完成項 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="33122-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="33122-121">同樣地， <xref:System.AppDomain> 在其堆疊中的所有線程都會接收 a `ThreadAbortException` ，但 `catch` 只 `finally` 會執行標示為的和區塊 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="33122-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="33122-122">指定應擲回適用于條件的例外狀況，例如記憶體不足、緩衝區溢位等。</span><span class="sxs-lookup"><span data-stu-id="33122-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="33122-123">指定應該卸載 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="33122-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="33122-124">CLR 會嘗試執行完成項。</span><span class="sxs-lookup"><span data-stu-id="33122-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33122-125">備註</span><span class="sxs-lookup"><span data-stu-id="33122-125">Remarks</span></span>  

 <span data-ttu-id="33122-126">主機會藉由呼叫 [ICLRPolicyManager](iclrpolicymanager-interface.md) 介面的方法來設定原則動作。</span><span class="sxs-lookup"><span data-stu-id="33122-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="33122-127">如需有關強制性和正常中止的詳細資訊，請參閱 [EClrOperation](eclroperation-enumeration.md) 列舉。</span><span class="sxs-lookup"><span data-stu-id="33122-127">For information about rude and graceful aborts, see the [EClrOperation](eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33122-128">需求</span><span class="sxs-lookup"><span data-stu-id="33122-128">Requirements</span></span>  

 <span data-ttu-id="33122-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33122-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33122-130">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="33122-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33122-131">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33122-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33122-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33122-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33122-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33122-133">See also</span></span>

- [<span data-ttu-id="33122-134">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="33122-134">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="33122-135">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="33122-135">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="33122-136">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="33122-136">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="33122-137">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="33122-137">Hosting Enumerations</span></span>](hosting-enumerations.md)
