---
title: "EInitializeNewDomainFlags 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EInitializeNewDomainFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: EInitializeNewDomainFlags
helpviewer_keywords: EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bee1c5086502a9675e8149e7d6c9bc72f573815c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="6211f-102">EInitializeNewDomainFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="6211f-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="6211f-103">可讓主機提供的執行階段相關的應用程式定義域初始化資訊。</span><span class="sxs-lookup"><span data-stu-id="6211f-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6211f-104">語法</span><span class="sxs-lookup"><span data-stu-id="6211f-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="6211f-105">成員</span><span class="sxs-lookup"><span data-stu-id="6211f-105">Members</span></span>  
  
|<span data-ttu-id="6211f-106">成員</span><span class="sxs-lookup"><span data-stu-id="6211f-106">Member</span></span>|<span data-ttu-id="6211f-107">說明</span><span class="sxs-lookup"><span data-stu-id="6211f-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="6211f-108">沒有旗標。</span><span class="sxs-lookup"><span data-stu-id="6211f-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="6211f-109">通知 common language runtime (CLR) 的主機不會變更應用程式定義域中的安全性狀態<xref:System.AppDomainManager.InitializeNewDomain%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="6211f-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6211f-110">備註</span><span class="sxs-lookup"><span data-stu-id="6211f-110">Remarks</span></span>  
 <span data-ttu-id="6211f-111">[Iclrdomainmanager:: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)方法使用的型別參數`EInitializeNewDomainFlags`。</span><span class="sxs-lookup"><span data-stu-id="6211f-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6211f-112">需求</span><span class="sxs-lookup"><span data-stu-id="6211f-112">Requirements</span></span>  
 <span data-ttu-id="6211f-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6211f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6211f-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6211f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6211f-115">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6211f-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6211f-116">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6211f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6211f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6211f-117">See Also</span></span>  
 [<span data-ttu-id="6211f-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="6211f-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="6211f-119">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="6211f-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
