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
ms.openlocfilehash: acf449014f5bf5683d5488f8ed2ead963676fe6b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728325"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="58f09-102">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="58f09-102">ICLRControl Interface</span></span>

<span data-ttu-id="58f09-103">提供的方法可讓主機取得 common language runtime (CLR) 的參考，以及設定這些層面。</span><span class="sxs-lookup"><span data-stu-id="58f09-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58f09-104">方法</span><span class="sxs-lookup"><span data-stu-id="58f09-104">Methods</span></span>  
  
|<span data-ttu-id="58f09-105">方法</span><span class="sxs-lookup"><span data-stu-id="58f09-105">Method</span></span>|<span data-ttu-id="58f09-106">描述</span><span class="sxs-lookup"><span data-stu-id="58f09-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58f09-107">GetCLRManager 方法</span><span class="sxs-lookup"><span data-stu-id="58f09-107">GetCLRManager Method</span></span>](iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="58f09-108">取得主機可用來設定 CLR 之任何管理員類型之實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="58f09-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="58f09-109">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="58f09-109">SetAppDomainManagerType Method</span></span>](iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="58f09-110">將衍生自的型別設定 <xref:System.AppDomainManager> 為應用程式域管理員的型別。</span><span class="sxs-lookup"><span data-stu-id="58f09-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58f09-111">需求</span><span class="sxs-lookup"><span data-stu-id="58f09-111">Requirements</span></span>  

 <span data-ttu-id="58f09-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58f09-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58f09-113">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="58f09-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58f09-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="58f09-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58f09-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58f09-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f09-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58f09-116">See also</span></span>

- [<span data-ttu-id="58f09-117">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="58f09-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="58f09-118">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="58f09-118">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="58f09-119">ICLRGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="58f09-119">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="58f09-120">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="58f09-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="58f09-121">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="58f09-121">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="58f09-122">ICLROnEventManager 介面</span><span class="sxs-lookup"><span data-stu-id="58f09-122">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="58f09-123">ICLRPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="58f09-123">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="58f09-124">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="58f09-124">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="58f09-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="58f09-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
