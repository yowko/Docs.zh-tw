---
title: ICLRControl 介面
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f70e7958cc9ac198738ed72732fe7b6563c89067
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175418"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="637ae-102">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="637ae-102">ICLRControl Interface</span></span>
<span data-ttu-id="637ae-103">提供可供主應用程式能夠取得參考，以及設定方面的 common language runtime (CLR) 方法。</span><span class="sxs-lookup"><span data-stu-id="637ae-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="637ae-104">方法</span><span class="sxs-lookup"><span data-stu-id="637ae-104">Methods</span></span>  
  
|<span data-ttu-id="637ae-105">方法</span><span class="sxs-lookup"><span data-stu-id="637ae-105">Method</span></span>|<span data-ttu-id="637ae-106">描述</span><span class="sxs-lookup"><span data-stu-id="637ae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="637ae-107">GetCLRManager 方法</span><span class="sxs-lookup"><span data-stu-id="637ae-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="637ae-108">取得執行個體的任何主機可以用來設定 CLR 管理員類型的介面指標。</span><span class="sxs-lookup"><span data-stu-id="637ae-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="637ae-109">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="637ae-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="637ae-110">設定型別衍生自<xref:System.AppDomainManager>做為應用程式定義域管理員類型。</span><span class="sxs-lookup"><span data-stu-id="637ae-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="637ae-111">需求</span><span class="sxs-lookup"><span data-stu-id="637ae-111">Requirements</span></span>  
 <span data-ttu-id="637ae-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="637ae-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="637ae-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="637ae-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="637ae-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="637ae-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="637ae-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="637ae-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="637ae-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="637ae-116">See also</span></span>

- [<span data-ttu-id="637ae-117">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="637ae-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="637ae-118">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="637ae-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="637ae-119">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="637ae-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="637ae-120">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="637ae-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="637ae-121">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="637ae-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="637ae-122">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="637ae-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="637ae-123">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="637ae-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="637ae-124">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="637ae-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="637ae-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="637ae-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
