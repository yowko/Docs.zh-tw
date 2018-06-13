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
ms.openlocfilehash: 0175ab1d06a8166a5bbfd0c42018085a801740f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431445"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="ffba0-102">EInitializeNewDomainFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="ffba0-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="ffba0-103">可讓主機提供的執行階段相關的應用程式定義域初始化資訊。</span><span class="sxs-lookup"><span data-stu-id="ffba0-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffba0-104">語法</span><span class="sxs-lookup"><span data-stu-id="ffba0-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="ffba0-105">成員</span><span class="sxs-lookup"><span data-stu-id="ffba0-105">Members</span></span>  
  
|<span data-ttu-id="ffba0-106">成員</span><span class="sxs-lookup"><span data-stu-id="ffba0-106">Member</span></span>|<span data-ttu-id="ffba0-107">描述</span><span class="sxs-lookup"><span data-stu-id="ffba0-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="ffba0-108">沒有旗標。</span><span class="sxs-lookup"><span data-stu-id="ffba0-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="ffba0-109">通知 common language runtime (CLR) 的主機不會變更應用程式定義域中的安全性狀態<xref:System.AppDomainManager.InitializeNewDomain%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="ffba0-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffba0-110">備註</span><span class="sxs-lookup"><span data-stu-id="ffba0-110">Remarks</span></span>  
 <span data-ttu-id="ffba0-111">[Iclrdomainmanager:: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)方法使用的型別參數`EInitializeNewDomainFlags`。</span><span class="sxs-lookup"><span data-stu-id="ffba0-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffba0-112">需求</span><span class="sxs-lookup"><span data-stu-id="ffba0-112">Requirements</span></span>  
 <span data-ttu-id="ffba0-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ffba0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffba0-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ffba0-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffba0-115">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ffba0-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffba0-116">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffba0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffba0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffba0-117">See Also</span></span>  
 [<span data-ttu-id="ffba0-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="ffba0-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="ffba0-119">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="ffba0-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
