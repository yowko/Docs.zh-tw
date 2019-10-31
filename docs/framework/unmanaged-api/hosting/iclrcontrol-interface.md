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
ms.openlocfilehash: 914a2f6103fb0ffb9a7b9fcb895ecf0cd62f3c43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126600"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="34b79-102">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="34b79-102">ICLRControl Interface</span></span>
<span data-ttu-id="34b79-103">提供的方法可讓主機取得通用語言執行時間（CLR）的參考，並設定的各個層面。</span><span class="sxs-lookup"><span data-stu-id="34b79-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="34b79-104">方法</span><span class="sxs-lookup"><span data-stu-id="34b79-104">Methods</span></span>  
  
|<span data-ttu-id="34b79-105">方法</span><span class="sxs-lookup"><span data-stu-id="34b79-105">Method</span></span>|<span data-ttu-id="34b79-106">描述</span><span class="sxs-lookup"><span data-stu-id="34b79-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="34b79-107">GetCLRManager 方法</span><span class="sxs-lookup"><span data-stu-id="34b79-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="34b79-108">取得主機可以用來設定 CLR 之任何管理員類型的實例介面指標。</span><span class="sxs-lookup"><span data-stu-id="34b79-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="34b79-109">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="34b79-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="34b79-110">設定衍生自 <xref:System.AppDomainManager> 的類型，做為應用程式域管理員的類型。</span><span class="sxs-lookup"><span data-stu-id="34b79-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34b79-111">需求</span><span class="sxs-lookup"><span data-stu-id="34b79-111">Requirements</span></span>  
 <span data-ttu-id="34b79-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34b79-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34b79-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="34b79-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34b79-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="34b79-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34b79-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34b79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b79-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="34b79-116">See also</span></span>

- [<span data-ttu-id="34b79-117">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="34b79-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="34b79-118">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="34b79-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="34b79-119">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="34b79-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="34b79-120">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="34b79-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="34b79-121">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="34b79-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="34b79-122">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="34b79-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="34b79-123">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="34b79-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="34b79-124">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="34b79-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="34b79-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="34b79-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
