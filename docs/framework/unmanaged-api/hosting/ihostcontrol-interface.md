---
title: "IHostControl 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d0eaecef4cc34549c7d37953a5c8144bdd983692
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="d64e1-102">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="d64e1-102">IHostControl Interface</span></span>
<span data-ttu-id="d64e1-103">提供設定載入的組件，以及判斷哪些裝載介面主應用程式支援的方法。</span><span class="sxs-lookup"><span data-stu-id="d64e1-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d64e1-104">方法</span><span class="sxs-lookup"><span data-stu-id="d64e1-104">Methods</span></span>  
  
|<span data-ttu-id="d64e1-105">方法</span><span class="sxs-lookup"><span data-stu-id="d64e1-105">Method</span></span>|<span data-ttu-id="d64e1-106">描述</span><span class="sxs-lookup"><span data-stu-id="d64e1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d64e1-107">GetHostManager 方法</span><span class="sxs-lookup"><span data-stu-id="d64e1-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="d64e1-108">取得具有指定的介面指標主機的介面實作`IID`。</span><span class="sxs-lookup"><span data-stu-id="d64e1-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="d64e1-109">SetAppDomainManager 方法</span><span class="sxs-lookup"><span data-stu-id="d64e1-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="d64e1-110">通知主機已建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="d64e1-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d64e1-111">需求</span><span class="sxs-lookup"><span data-stu-id="d64e1-111">Requirements</span></span>  
 <span data-ttu-id="d64e1-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d64e1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d64e1-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d64e1-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d64e1-114">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d64e1-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d64e1-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d64e1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d64e1-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="d64e1-116">See Also</span></span>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="d64e1-117">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="d64e1-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="d64e1-118">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="d64e1-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="d64e1-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d64e1-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
