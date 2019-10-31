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
ms.openlocfilehash: 3693285e13d0650f7662e2187471027cc4c40704
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129423"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="f053a-102">EInitializeNewDomainFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="f053a-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="f053a-103">讓主機為執行時間提供初始化應用程式域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f053a-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f053a-104">語法</span><span class="sxs-lookup"><span data-stu-id="f053a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f053a-105">Members</span><span class="sxs-lookup"><span data-stu-id="f053a-105">Members</span></span>  
  
|<span data-ttu-id="f053a-106">成員</span><span class="sxs-lookup"><span data-stu-id="f053a-106">Member</span></span>|<span data-ttu-id="f053a-107">描述</span><span class="sxs-lookup"><span data-stu-id="f053a-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="f053a-108">沒有旗標。</span><span class="sxs-lookup"><span data-stu-id="f053a-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="f053a-109">通知 common language runtime （CLR），主機不會對 <xref:System.AppDomainManager.InitializeNewDomain%2A> 方法中應用程式域的安全性狀態進行變更。</span><span class="sxs-lookup"><span data-stu-id="f053a-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f053a-110">備註</span><span class="sxs-lookup"><span data-stu-id="f053a-110">Remarks</span></span>  
 <span data-ttu-id="f053a-111">[ICLRDomainManager：： SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)方法會接受 `EInitializeNewDomainFlags`類型的參數。</span><span class="sxs-lookup"><span data-stu-id="f053a-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f053a-112">需求</span><span class="sxs-lookup"><span data-stu-id="f053a-112">Requirements</span></span>  
 <span data-ttu-id="f053a-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f053a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f053a-114">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="f053a-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f053a-115">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="f053a-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f053a-116">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f053a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f053a-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="f053a-117">See also</span></span>

- [<span data-ttu-id="f053a-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="f053a-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="f053a-119">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="f053a-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
