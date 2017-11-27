---
title: "ICLRPolicyManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager
helpviewer_keywords: ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3dd904184b730a5b0f5b2dfcac4197e708544d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="e6088-102">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="e6088-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="e6088-103">提供方法，讓主應用程式指定原則發生失敗和逾時所要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="e6088-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6088-104">方法</span><span class="sxs-lookup"><span data-stu-id="e6088-104">Methods</span></span>  
  
|<span data-ttu-id="e6088-105">方法</span><span class="sxs-lookup"><span data-stu-id="e6088-105">Method</span></span>|<span data-ttu-id="e6088-106">說明</span><span class="sxs-lookup"><span data-stu-id="e6088-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6088-107">SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="e6088-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="e6088-108">指定發生指定的失敗時，應該採取 common language runtime (CLR) 的原則動作。</span><span class="sxs-lookup"><span data-stu-id="e6088-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="e6088-109">SetActionOnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="e6088-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="e6088-110">指定 CLR 在指定的作業逾時應該採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="e6088-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="e6088-111">SetDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="e6088-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="e6088-112">指定 CLR 在發生指定的作業時應該採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="e6088-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="e6088-113">SetTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="e6088-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="e6088-114">設定指定之作業的逾時值。</span><span class="sxs-lookup"><span data-stu-id="e6088-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="e6088-115">SetTimeoutAndAction 方法</span><span class="sxs-lookup"><span data-stu-id="e6088-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="e6088-116">設定指定的作業的逾時值，並指定 CLR 在發生作業時應該採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="e6088-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="e6088-117">SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="e6088-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="e6088-118">發生未處理的例外狀況時，請指定 CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="e6088-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6088-119">需求</span><span class="sxs-lookup"><span data-stu-id="e6088-119">Requirements</span></span>  
 <span data-ttu-id="e6088-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6088-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6088-121">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e6088-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6088-122">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e6088-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6088-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6088-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6088-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6088-124">See Also</span></span>  
 [<span data-ttu-id="e6088-125">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="e6088-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="e6088-126">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="e6088-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="e6088-127">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="e6088-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="e6088-128">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="e6088-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
