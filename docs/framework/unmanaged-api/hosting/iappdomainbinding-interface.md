---
title: "IAppDomainBinding 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppDomainBinding
api_location: mscoree.dll
api_type: COM
f1_keywords: IAppDomainBinding
helpviewer_keywords: IAppDomainBinding interface [.NET Framework hosting]
ms.assetid: 368881ab-c4ea-4731-bf22-c596aac7c66c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a6f26c8337f89d829f42e00a9e5e79731a15156
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="a1e2e-102">IAppDomainBinding 介面</span><span class="sxs-lookup"><span data-stu-id="a1e2e-102">IAppDomainBinding Interface</span></span>
<span data-ttu-id="a1e2e-103">提供稱為 common language runtime (CLR)，以通知主機應用程式已建立應用程式定義域的方法。</span><span class="sxs-lookup"><span data-stu-id="a1e2e-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1e2e-104">方法</span><span class="sxs-lookup"><span data-stu-id="a1e2e-104">Methods</span></span>  
  
|<span data-ttu-id="a1e2e-105">方法</span><span class="sxs-lookup"><span data-stu-id="a1e2e-105">Method</span></span>|<span data-ttu-id="a1e2e-106">描述</span><span class="sxs-lookup"><span data-stu-id="a1e2e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1e2e-107">OnAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="a1e2e-107">OnAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="a1e2e-108">由 common language runtime (CLR)，以通知主機已建立應用程式定義域呼叫。</span><span class="sxs-lookup"><span data-stu-id="a1e2e-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1e2e-109">需求</span><span class="sxs-lookup"><span data-stu-id="a1e2e-109">Requirements</span></span>  
 <span data-ttu-id="a1e2e-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e2e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1e2e-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a1e2e-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1e2e-112">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a1e2e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1e2e-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1e2e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e2e-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="a1e2e-114">See Also</span></span>  
 [<span data-ttu-id="a1e2e-115">裝載介面</span><span class="sxs-lookup"><span data-stu-id="a1e2e-115">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
