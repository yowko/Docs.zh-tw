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
ms.openlocfilehash: 652739ad51e0a177f7b0fc6c0c9a11508c820bb3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721718"
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="5f762-102">IAppDomainBinding 介面</span><span class="sxs-lookup"><span data-stu-id="5f762-102">IAppDomainBinding Interface</span></span>

<span data-ttu-id="5f762-103">提供由 common language runtime (CLR) 所呼叫的方法，以通知主應用程式已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="5f762-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f762-104">方法</span><span class="sxs-lookup"><span data-stu-id="5f762-104">Methods</span></span>  
  
|<span data-ttu-id="5f762-105">方法</span><span class="sxs-lookup"><span data-stu-id="5f762-105">Method</span></span>|<span data-ttu-id="5f762-106">描述</span><span class="sxs-lookup"><span data-stu-id="5f762-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f762-107">OnAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="5f762-107">OnAppDomain Method</span></span>](iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="5f762-108">由 common language runtime (CLR) 呼叫，以通知主機已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="5f762-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f762-109">需求</span><span class="sxs-lookup"><span data-stu-id="5f762-109">Requirements</span></span>  

 <span data-ttu-id="5f762-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f762-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f762-111">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5f762-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f762-112">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="5f762-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f762-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f762-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f762-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f762-114">See also</span></span>

- [<span data-ttu-id="5f762-115">裝載介面</span><span class="sxs-lookup"><span data-stu-id="5f762-115">Hosting Interfaces</span></span>](hosting-interfaces.md)
