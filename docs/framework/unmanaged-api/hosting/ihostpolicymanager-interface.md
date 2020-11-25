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
ms.openlocfilehash: 3c85bcbe8aee453b19217ebd1f48feea113e3bb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731213"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="9b7e7-102">IHostPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="9b7e7-102">IHostPolicyManager Interface</span></span>

<span data-ttu-id="9b7e7-103">提供方法，以通知主機 common language runtime (CLR) 在中止、超時或失敗時所執行的動作。</span><span class="sxs-lookup"><span data-stu-id="9b7e7-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b7e7-104">方法</span><span class="sxs-lookup"><span data-stu-id="9b7e7-104">Methods</span></span>  
  
|<span data-ttu-id="9b7e7-105">方法</span><span class="sxs-lookup"><span data-stu-id="9b7e7-105">Method</span></span>|<span data-ttu-id="9b7e7-106">描述</span><span class="sxs-lookup"><span data-stu-id="9b7e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b7e7-107">OnDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="9b7e7-107">OnDefaultAction Method</span></span>](ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="9b7e7-108">通知主機，CLR 即將採用呼叫 [ICLRPolicyManager：： SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) 所指定的預設動作，以回應執行緒中止或卸載 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="9b7e7-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="9b7e7-109">OnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="9b7e7-109">OnFailure Method</span></span>](ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="9b7e7-110">通知主機 CLR 即將採取呼叫 [ICLRPolicyManager：： SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) 所指定的動作，以回應資源配置或回收失敗。</span><span class="sxs-lookup"><span data-stu-id="9b7e7-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="9b7e7-111">OnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="9b7e7-111">OnTimeout Method</span></span>](ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="9b7e7-112">通知主機，CLR 即將採取呼叫 [ICLRPolicyManager：： SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) 所指定的動作，以回應超時。</span><span class="sxs-lookup"><span data-stu-id="9b7e7-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b7e7-113">需求</span><span class="sxs-lookup"><span data-stu-id="9b7e7-113">Requirements</span></span>  

 <span data-ttu-id="9b7e7-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b7e7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b7e7-115">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9b7e7-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b7e7-116">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="9b7e7-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b7e7-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b7e7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7e7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b7e7-118">See also</span></span>

- [<span data-ttu-id="9b7e7-119">EClrFailure 列舉</span><span class="sxs-lookup"><span data-stu-id="9b7e7-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="9b7e7-120">EClrOperation 列舉</span><span class="sxs-lookup"><span data-stu-id="9b7e7-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="9b7e7-121">EPolicyAction 列舉</span><span class="sxs-lookup"><span data-stu-id="9b7e7-121">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="9b7e7-122">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="9b7e7-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="9b7e7-123">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9b7e7-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
