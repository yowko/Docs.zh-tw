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
ms.openlocfilehash: db089a55128fa675ceedf157b046fe205d8c6b51
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804334"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="8992e-102">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="8992e-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="8992e-103">提供方法，以通知主機 common language runtime （CLR）在中止、超時或失敗時所執行的動作。</span><span class="sxs-lookup"><span data-stu-id="8992e-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8992e-104">方法</span><span class="sxs-lookup"><span data-stu-id="8992e-104">Methods</span></span>  
  
|<span data-ttu-id="8992e-105">方法</span><span class="sxs-lookup"><span data-stu-id="8992e-105">Method</span></span>|<span data-ttu-id="8992e-106">描述</span><span class="sxs-lookup"><span data-stu-id="8992e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8992e-107">OnDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="8992e-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="8992e-108">通知主機 CLR 即將採取[ICLRPolicyManager：： SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md)呼叫所指定的預設動作，以回應執行緒中止或卸載 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="8992e-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="8992e-109">OnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="8992e-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="8992e-110">通知主機 CLR 即將採取[ICLRPolicyManager：： SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md)呼叫所指定的動作，以回應資源配置或回收失敗。</span><span class="sxs-lookup"><span data-stu-id="8992e-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="8992e-111">OnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="8992e-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="8992e-112">通知主機 CLR 即將採取[ICLRPolicyManager：： SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md)呼叫所指定的動作，以回應超時。</span><span class="sxs-lookup"><span data-stu-id="8992e-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8992e-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="8992e-113">Requirements</span></span>  
 <span data-ttu-id="8992e-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8992e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8992e-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="8992e-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8992e-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8992e-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8992e-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8992e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8992e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8992e-118">See also</span></span>

- [<span data-ttu-id="8992e-119">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="8992e-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="8992e-120">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="8992e-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="8992e-121">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="8992e-121">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="8992e-122">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="8992e-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="8992e-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="8992e-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
