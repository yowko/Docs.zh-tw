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
ms.openlocfilehash: 7ff10f84d8d270d31c5d560fb3c9bd3c81cf3e24
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616225"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="89f28-102">EInitializeNewDomainFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="89f28-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="89f28-103">讓主機為執行時間提供初始化應用程式域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="89f28-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89f28-104">語法</span><span class="sxs-lookup"><span data-stu-id="89f28-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="89f28-105">成員</span><span class="sxs-lookup"><span data-stu-id="89f28-105">Members</span></span>  
  
|<span data-ttu-id="89f28-106">成員</span><span class="sxs-lookup"><span data-stu-id="89f28-106">Member</span></span>|<span data-ttu-id="89f28-107">說明</span><span class="sxs-lookup"><span data-stu-id="89f28-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="89f28-108">沒有旗標。</span><span class="sxs-lookup"><span data-stu-id="89f28-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="89f28-109">通知 common language runtime （CLR），主機不會對方法中應用程式域的安全性狀態進行變更 <xref:System.AppDomainManager.InitializeNewDomain%2A> 。</span><span class="sxs-lookup"><span data-stu-id="89f28-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89f28-110">備註</span><span class="sxs-lookup"><span data-stu-id="89f28-110">Remarks</span></span>  
 <span data-ttu-id="89f28-111">[ICLRDomainManager：： SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md)方法接受型別為的參數 `EInitializeNewDomainFlags` 。</span><span class="sxs-lookup"><span data-stu-id="89f28-111">The [ICLRDomainManager::SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89f28-112">需求</span><span class="sxs-lookup"><span data-stu-id="89f28-112">Requirements</span></span>  
 <span data-ttu-id="89f28-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89f28-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89f28-114">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="89f28-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89f28-115">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="89f28-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89f28-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89f28-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f28-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89f28-117">See also</span></span>

- [<span data-ttu-id="89f28-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="89f28-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="89f28-119">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="89f28-119">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)
