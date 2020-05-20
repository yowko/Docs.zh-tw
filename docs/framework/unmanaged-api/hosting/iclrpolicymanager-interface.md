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
ms.openlocfilehash: 631301a10aee96bb00aeda6b0b8695f0aea186a8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703484"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="8ce40-102">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="8ce40-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="8ce40-103">提供的方法可讓主機指定發生失敗和超時事件時所要採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="8ce40-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8ce40-104">方法</span><span class="sxs-lookup"><span data-stu-id="8ce40-104">Methods</span></span>  
  
|<span data-ttu-id="8ce40-105">方法</span><span class="sxs-lookup"><span data-stu-id="8ce40-105">Method</span></span>|<span data-ttu-id="8ce40-106">描述</span><span class="sxs-lookup"><span data-stu-id="8ce40-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8ce40-107">SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="8ce40-107">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="8ce40-108">指定當發生指定的失敗時，common language runtime （CLR）應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="8ce40-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="8ce40-109">SetActionOnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="8ce40-109">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="8ce40-110">指定當指定的作業超時時，CLR 應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="8ce40-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="8ce40-111">SetDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="8ce40-111">SetDefaultAction Method</span></span>](iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="8ce40-112">指定當發生指定的作業時，CLR 應採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="8ce40-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="8ce40-113">SetTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="8ce40-113">SetTimeout Method</span></span>](iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="8ce40-114">設定指定之作業的超時值。</span><span class="sxs-lookup"><span data-stu-id="8ce40-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="8ce40-115">SetTimeoutAndAction 方法</span><span class="sxs-lookup"><span data-stu-id="8ce40-115">SetTimeoutAndAction Method</span></span>](iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="8ce40-116">設定指定之作業的超時值，並指定當作業發生時，CLR 應該採取的原則動作。</span><span class="sxs-lookup"><span data-stu-id="8ce40-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="8ce40-117">SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="8ce40-117">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="8ce40-118">指定發生未處理的例外狀況時，CLR 的行為。</span><span class="sxs-lookup"><span data-stu-id="8ce40-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ce40-119">需求</span><span class="sxs-lookup"><span data-stu-id="8ce40-119">Requirements</span></span>  
 <span data-ttu-id="8ce40-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ce40-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ce40-121">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="8ce40-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ce40-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8ce40-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ce40-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ce40-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce40-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ce40-124">See also</span></span>

- [<span data-ttu-id="8ce40-125">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="8ce40-125">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="8ce40-126">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="8ce40-126">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="8ce40-127">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="8ce40-127">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="8ce40-128">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="8ce40-128">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
