---
title: EApiCategories 列舉
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41513d9b6f98743bfad95e4d9606cfb4927369e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769786"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="6727d-102">EApiCategories 列舉</span><span class="sxs-lookup"><span data-stu-id="6727d-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="6727d-103">描述分類的主機可以封鎖無法在部分信任程式碼中執行的功能。</span><span class="sxs-lookup"><span data-stu-id="6727d-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6727d-104">語法</span><span class="sxs-lookup"><span data-stu-id="6727d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a><span data-ttu-id="6727d-105">成員</span><span class="sxs-lookup"><span data-stu-id="6727d-105">Members</span></span>  
  
|<span data-ttu-id="6727d-106">成員</span><span class="sxs-lookup"><span data-stu-id="6727d-106">Member</span></span>|<span data-ttu-id="6727d-107">描述</span><span class="sxs-lookup"><span data-stu-id="6727d-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="6727d-108">指定所有 managed 類別和成員所涵蓋的其他`EApiCategories`欄位遭到封鎖而無法在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="6727d-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="6727d-109">指定封鎖受管理的類別和成員，可讓建立、 管理和解構的外部處理序在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="6727d-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="6727d-110">指定 managed 的類別和成員，可讓建立、 管理和解構的外部執行緒被封鎖而無法執行部分信任程式碼中。</span><span class="sxs-lookup"><span data-stu-id="6727d-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="6727d-111">指定封鎖受管理的類型和成員，可能會洩漏中止上的記憶體在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="6727d-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="6727d-112">指定沒有任何 managed 程式碼類別無法在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="6727d-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="6727d-113">指定通用語言執行平台 (CLR) 安全性基礎結構遭到封鎖而無法由部分信任程式碼。</span><span class="sxs-lookup"><span data-stu-id="6727d-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="6727d-114">指定封鎖受管理的類別和其功能可能會影響裝載的處理序的成員在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="6727d-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="6727d-115">指定封鎖受管理的類別和其功能可能會影響裝載處理序中的執行緒的成員在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="6727d-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="6727d-116">指定封鎖受管理的類別和公開共用的狀態的成員在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="6727d-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="6727d-117">指定封鎖 common language runtime 類別和成員，可讓使用者程式碼保留鎖定在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="6727d-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="6727d-118">指定封鎖受管理的類別和成員允許或需要人為互動在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="6727d-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6727d-119">備註</span><span class="sxs-lookup"><span data-stu-id="6727d-119">Remarks</span></span>  
 <span data-ttu-id="6727d-120">[Iclrhostprotectionmanager:: Setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)方法會採用類型參數的`EApiCategories`。</span><span class="sxs-lookup"><span data-stu-id="6727d-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="6727d-121">`EApiCategories`列舉型別和`SetProtectedCategories`方法直接相關的 managed<xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="6727d-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="6727d-122">受管理的類別會搭配<xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>列舉型別，其值直接對應到`EApiCategories`值，以將 managed 型別和將功能對應至所描述的類別公開的成員標示`EApiCategories`。</span><span class="sxs-lookup"><span data-stu-id="6727d-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6727d-123">需求</span><span class="sxs-lookup"><span data-stu-id="6727d-123">Requirements</span></span>  
 <span data-ttu-id="6727d-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6727d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6727d-125">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6727d-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6727d-126">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6727d-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6727d-127">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6727d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6727d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6727d-128">See also</span></span>

- [<span data-ttu-id="6727d-129">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="6727d-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="6727d-130">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="6727d-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
