---
title: ICLRPolicyManager 介面
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 59aa904d4c67326b60381d3476eaab179d7fa42b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140799"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="ecc1e-102">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="ecc1e-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="ecc1e-103">提供的方法可讓主機指定發生失敗和超時事件時所要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="ecc1e-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ecc1e-104">方法</span><span class="sxs-lookup"><span data-stu-id="ecc1e-104">Methods</span></span>  
  
|<span data-ttu-id="ecc1e-105">方法</span><span class="sxs-lookup"><span data-stu-id="ecc1e-105">Method</span></span>|<span data-ttu-id="ecc1e-106">描述</span><span class="sxs-lookup"><span data-stu-id="ecc1e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ecc1e-107">SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="ecc1e-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="ecc1e-108">指定當發生指定的失敗時，common language runtime （CLR）應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="ecc1e-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="ecc1e-109">SetActionOnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="ecc1e-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="ecc1e-110">指定當指定的作業超時時，CLR 應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="ecc1e-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="ecc1e-111">SetDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="ecc1e-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="ecc1e-112">指定當發生指定的作業時，CLR 應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="ecc1e-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="ecc1e-113">SetTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="ecc1e-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="ecc1e-114">設定指定之作業的超時值。</span><span class="sxs-lookup"><span data-stu-id="ecc1e-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="ecc1e-115">SetTimeoutAndAction 方法</span><span class="sxs-lookup"><span data-stu-id="ecc1e-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="ecc1e-116">設定指定之作業的超時值，並指定當作業發生時，CLR 應該採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="ecc1e-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="ecc1e-117">SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="ecc1e-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="ecc1e-118">指定發生未處理的例外狀況時，CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="ecc1e-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ecc1e-119">需求</span><span class="sxs-lookup"><span data-stu-id="ecc1e-119">Requirements</span></span>  
 <span data-ttu-id="ecc1e-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ecc1e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecc1e-121">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ecc1e-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecc1e-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ecc1e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecc1e-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecc1e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc1e-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="ecc1e-124">See also</span></span>

- [<span data-ttu-id="ecc1e-125">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="ecc1e-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="ecc1e-126">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="ecc1e-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="ecc1e-127">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="ecc1e-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="ecc1e-128">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="ecc1e-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
