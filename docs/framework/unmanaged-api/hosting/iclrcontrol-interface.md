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
ms.openlocfilehash: 54748fdeaf911591c21f4495335e54c777878f04
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615830"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="40c34-102">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="40c34-102">ICLRControl Interface</span></span>
<span data-ttu-id="40c34-103">提供的方法可讓主機取得通用語言執行時間（CLR）的參考，並設定的各個層面。</span><span class="sxs-lookup"><span data-stu-id="40c34-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40c34-104">方法</span><span class="sxs-lookup"><span data-stu-id="40c34-104">Methods</span></span>  
  
|<span data-ttu-id="40c34-105">方法</span><span class="sxs-lookup"><span data-stu-id="40c34-105">Method</span></span>|<span data-ttu-id="40c34-106">描述</span><span class="sxs-lookup"><span data-stu-id="40c34-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40c34-107">GetCLRManager 方法</span><span class="sxs-lookup"><span data-stu-id="40c34-107">GetCLRManager Method</span></span>](iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="40c34-108">取得主機可以用來設定 CLR 之任何管理員類型的實例介面指標。</span><span class="sxs-lookup"><span data-stu-id="40c34-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="40c34-109">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="40c34-109">SetAppDomainManagerType Method</span></span>](iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="40c34-110">將衍生自的類型設定 <xref:System.AppDomainManager> 為應用程式域管理員的類型。</span><span class="sxs-lookup"><span data-stu-id="40c34-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40c34-111">需求</span><span class="sxs-lookup"><span data-stu-id="40c34-111">Requirements</span></span>  
 <span data-ttu-id="40c34-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="40c34-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40c34-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="40c34-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40c34-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="40c34-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40c34-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40c34-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c34-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40c34-116">See also</span></span>

- [<span data-ttu-id="40c34-117">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="40c34-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="40c34-118">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="40c34-118">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="40c34-119">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="40c34-119">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="40c34-120">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="40c34-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="40c34-121">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="40c34-121">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="40c34-122">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="40c34-122">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="40c34-123">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="40c34-123">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="40c34-124">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="40c34-124">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="40c34-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="40c34-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
