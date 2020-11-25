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
ms.openlocfilehash: 8350b507609e63c060cda08514200d386c37a6b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724321"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="05eb8-102">EInitializeNewDomainFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="05eb8-102">EInitializeNewDomainFlags Enumeration</span></span>

<span data-ttu-id="05eb8-103">讓主機提供執行時間的相關資訊，以初始化應用程式域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="05eb8-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05eb8-104">語法</span><span class="sxs-lookup"><span data-stu-id="05eb8-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="05eb8-105">成員</span><span class="sxs-lookup"><span data-stu-id="05eb8-105">Members</span></span>  
  
|<span data-ttu-id="05eb8-106">member</span><span class="sxs-lookup"><span data-stu-id="05eb8-106">Member</span></span>|<span data-ttu-id="05eb8-107">描述</span><span class="sxs-lookup"><span data-stu-id="05eb8-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="05eb8-108">沒有旗標。</span><span class="sxs-lookup"><span data-stu-id="05eb8-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="05eb8-109">通知 common language runtime (CLR) 主機將不會變更方法中應用程式域的安全性狀態 <xref:System.AppDomainManager.InitializeNewDomain%2A> 。</span><span class="sxs-lookup"><span data-stu-id="05eb8-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05eb8-110">備註</span><span class="sxs-lookup"><span data-stu-id="05eb8-110">Remarks</span></span>  

 <span data-ttu-id="05eb8-111">[ICLRDomainManager：： SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md)方法接受型別為的參數 `EInitializeNewDomainFlags` 。</span><span class="sxs-lookup"><span data-stu-id="05eb8-111">The [ICLRDomainManager::SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05eb8-112">需求</span><span class="sxs-lookup"><span data-stu-id="05eb8-112">Requirements</span></span>  

 <span data-ttu-id="05eb8-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05eb8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05eb8-114">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="05eb8-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05eb8-115">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05eb8-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05eb8-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05eb8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05eb8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05eb8-117">See also</span></span>

- [<span data-ttu-id="05eb8-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="05eb8-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="05eb8-119">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="05eb8-119">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)
