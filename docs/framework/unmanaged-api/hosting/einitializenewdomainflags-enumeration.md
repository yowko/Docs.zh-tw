---
title: EInitializeNewDomainFlags 列舉
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04b0d9989d66888c33de0359e4c93529fcfbf8d1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095356"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="7974f-102">EInitializeNewDomainFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="7974f-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="7974f-103">可讓主應用程式執行階段提供的應用程式定義域初始化資訊。</span><span class="sxs-lookup"><span data-stu-id="7974f-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7974f-104">語法</span><span class="sxs-lookup"><span data-stu-id="7974f-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="7974f-105">成員</span><span class="sxs-lookup"><span data-stu-id="7974f-105">Members</span></span>  
  
|<span data-ttu-id="7974f-106">成員</span><span class="sxs-lookup"><span data-stu-id="7974f-106">Member</span></span>|<span data-ttu-id="7974f-107">描述</span><span class="sxs-lookup"><span data-stu-id="7974f-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="7974f-108">沒有旗標。</span><span class="sxs-lookup"><span data-stu-id="7974f-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="7974f-109">會告知 common language runtime (CLR) 主機，將不進行變更的應用程式定義域的安全性狀態<xref:System.AppDomainManager.InitializeNewDomain%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="7974f-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7974f-110">備註</span><span class="sxs-lookup"><span data-stu-id="7974f-110">Remarks</span></span>  
 <span data-ttu-id="7974f-111">[Iclrdomainmanager:: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)方法會採用類型參數的`EInitializeNewDomainFlags`。</span><span class="sxs-lookup"><span data-stu-id="7974f-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7974f-112">需求</span><span class="sxs-lookup"><span data-stu-id="7974f-112">Requirements</span></span>  
 <span data-ttu-id="7974f-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7974f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7974f-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7974f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7974f-115">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7974f-115">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7974f-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="7974f-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7974f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7974f-117">See also</span></span>

- [<span data-ttu-id="7974f-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="7974f-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="7974f-119">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="7974f-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
