---
title: IAppDomainBinding 介面
ms.date: 03/30/2017
api_name:
- IAppDomainBinding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainBinding
helpviewer_keywords:
- IAppDomainBinding interface [.NET Framework hosting]
ms.assetid: 368881ab-c4ea-4731-bf22-c596aac7c66c
topic_type:
- apiref
ms.openlocfilehash: cf4fa9c5ec35391a0e772e25112f305bfa6e1564
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126894"
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="2429e-102">IAppDomainBinding 介面</span><span class="sxs-lookup"><span data-stu-id="2429e-102">IAppDomainBinding Interface</span></span>
<span data-ttu-id="2429e-103">提供通用語言執行時間（CLR）所呼叫的方法，以通知主應用程式已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="2429e-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2429e-104">方法</span><span class="sxs-lookup"><span data-stu-id="2429e-104">Methods</span></span>  
  
|<span data-ttu-id="2429e-105">方法</span><span class="sxs-lookup"><span data-stu-id="2429e-105">Method</span></span>|<span data-ttu-id="2429e-106">描述</span><span class="sxs-lookup"><span data-stu-id="2429e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2429e-107">OnAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="2429e-107">OnAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="2429e-108">由 common language runtime （CLR）呼叫，以通知主機已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="2429e-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2429e-109">需求</span><span class="sxs-lookup"><span data-stu-id="2429e-109">Requirements</span></span>  
 <span data-ttu-id="2429e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2429e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2429e-111">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2429e-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2429e-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2429e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2429e-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2429e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2429e-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="2429e-114">See also</span></span>

- [<span data-ttu-id="2429e-115">裝載介面</span><span class="sxs-lookup"><span data-stu-id="2429e-115">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
