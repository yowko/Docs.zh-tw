---
title: "EPolicyAction 列舉"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5de55d46eead37962fad7d7c1c5bd1766e772fe8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="ebf21-102">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="ebf21-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="ebf21-103">描述所描述的作業可以設定主機的原則動作[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)和所描述的失敗[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="ebf21-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf21-104">語法</span><span class="sxs-lookup"><span data-stu-id="ebf21-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="ebf21-105">成員</span><span class="sxs-lookup"><span data-stu-id="ebf21-105">Members</span></span>  
  
|<span data-ttu-id="ebf21-106">成員</span><span class="sxs-lookup"><span data-stu-id="ebf21-106">Member</span></span>|<span data-ttu-id="ebf21-107">描述</span><span class="sxs-lookup"><span data-stu-id="ebf21-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="ebf21-108">指定 common language runtime (CLR) 依正常程序應該中止的執行緒。</span><span class="sxs-lookup"><span data-stu-id="ebf21-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="ebf21-109">依正常程序中止包括嘗試執行所有`finally`封鎖任何`catch`區塊與執行緒中止與完成項。</span><span class="sxs-lookup"><span data-stu-id="ebf21-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="ebf21-110">指定 CLR 應該進入停用的狀態。</span><span class="sxs-lookup"><span data-stu-id="ebf21-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="ebf21-111">沒有進一步執行 managed 程式碼，在受影響的過程中，並進入 CLR 的執行緒會被封鎖。</span><span class="sxs-lookup"><span data-stu-id="ebf21-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="ebf21-112">指定 CLR 應該嘗試處理程序，包括執行完成項，以及執行清理和記錄作業的非失誤性結束。</span><span class="sxs-lookup"><span data-stu-id="ebf21-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="ebf21-113">指定的 CLR 程序會立即結束，而不需要執行完成項，或執行清除，以及記錄作業。</span><span class="sxs-lookup"><span data-stu-id="ebf21-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="ebf21-114">但是，傳送通知給偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ebf21-114">Nowever, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="ebf21-115">指定應該採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="ebf21-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="ebf21-116">指定 CLR 應該執行粗略的執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="ebf21-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="ebf21-117">只有`catch`和`finally`區塊標記為<xref:System.EnterpriseServices.MustRunInClientContextAttribute>會執行。</span><span class="sxs-lookup"><span data-stu-id="ebf21-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="ebf21-118">指定 CLR 應該結束處理程序，而不執行完成項，或作業記錄。</span><span class="sxs-lookup"><span data-stu-id="ebf21-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="ebf21-119">指定 CLR 應該執行的粗略卸載<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="ebf21-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="ebf21-120">只有完成項標記為<xref:System.EnterpriseServices.MustRunInClientContextAttribute>會執行。</span><span class="sxs-lookup"><span data-stu-id="ebf21-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="ebf21-121">同樣地，所有執行緒與這個<xref:System.AppDomain>其堆疊中接收`ThreadAbortException`，而是只有`catch`和`finally`區塊標記為<xref:System.EnterpriseServices.MustRunInClientContextAttribute>會執行。</span><span class="sxs-lookup"><span data-stu-id="ebf21-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="ebf21-122">指定應該擲回例外狀況，例如記憶體不足、 緩衝區溢位，以及其他等等。</span><span class="sxs-lookup"><span data-stu-id="ebf21-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="ebf21-123">指定<xref:System.AppDomain>應該卸載。</span><span class="sxs-lookup"><span data-stu-id="ebf21-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="ebf21-124">CLR 會嘗試執行完成項。</span><span class="sxs-lookup"><span data-stu-id="ebf21-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebf21-125">備註</span><span class="sxs-lookup"><span data-stu-id="ebf21-125">Remarks</span></span>  
 <span data-ttu-id="ebf21-126">主應用程式設定原則動作是呼叫的方法[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="ebf21-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="ebf21-127">中止粗略和依正常程序的相關資訊，請參閱[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="ebf21-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf21-128">需求</span><span class="sxs-lookup"><span data-stu-id="ebf21-128">Requirements</span></span>  
 <span data-ttu-id="ebf21-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ebf21-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf21-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ebf21-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ebf21-131">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ebf21-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebf21-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebf21-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf21-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="ebf21-133">See Also</span></span>  
 [<span data-ttu-id="ebf21-134">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="ebf21-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="ebf21-135">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="ebf21-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="ebf21-136">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="ebf21-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="ebf21-137">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="ebf21-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
