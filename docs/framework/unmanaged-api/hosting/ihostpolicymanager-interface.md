---
title: IHostPolicyManager 介面
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: 6ba7b7adc104db528293d77c3591370c6ce02c25
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128605"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="2bfd1-102">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="2bfd1-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="2bfd1-103">提供方法，以通知主機 common language runtime （CLR）在中止、超時或失敗時所執行的動作。</span><span class="sxs-lookup"><span data-stu-id="2bfd1-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2bfd1-104">方法</span><span class="sxs-lookup"><span data-stu-id="2bfd1-104">Methods</span></span>  
  
|<span data-ttu-id="2bfd1-105">方法</span><span class="sxs-lookup"><span data-stu-id="2bfd1-105">Method</span></span>|<span data-ttu-id="2bfd1-106">描述</span><span class="sxs-lookup"><span data-stu-id="2bfd1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2bfd1-107">OnDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="2bfd1-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="2bfd1-108">通知主機 CLR 即將採取[ICLRPolicyManager：： SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)呼叫所指定的預設動作，以回應執行緒中止或 <xref:System.AppDomain> 卸載。</span><span class="sxs-lookup"><span data-stu-id="2bfd1-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="2bfd1-109">OnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="2bfd1-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="2bfd1-110">通知主機 CLR 即將採取[ICLRPolicyManager：： SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)呼叫所指定的動作，以回應資源配置或回收失敗。</span><span class="sxs-lookup"><span data-stu-id="2bfd1-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="2bfd1-111">OnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="2bfd1-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="2bfd1-112">通知主機 CLR 即將採取[ICLRPolicyManager：： SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)呼叫所指定的動作，以回應超時。</span><span class="sxs-lookup"><span data-stu-id="2bfd1-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2bfd1-113">需求</span><span class="sxs-lookup"><span data-stu-id="2bfd1-113">Requirements</span></span>  
 <span data-ttu-id="2bfd1-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfd1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bfd1-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2bfd1-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2bfd1-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2bfd1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bfd1-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bfd1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bfd1-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="2bfd1-118">See also</span></span>

- [<span data-ttu-id="2bfd1-119">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="2bfd1-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="2bfd1-120">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="2bfd1-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="2bfd1-121">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="2bfd1-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="2bfd1-122">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="2bfd1-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="2bfd1-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="2bfd1-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
