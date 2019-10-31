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
ms.openlocfilehash: 0fd9409a5157e1013365c94f01631f130a76f54b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131206"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="93b29-102">EApiCategories 列舉</span><span class="sxs-lookup"><span data-stu-id="93b29-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="93b29-103">描述主機可以封鎖在部分信任程式碼中執行的功能類別。</span><span class="sxs-lookup"><span data-stu-id="93b29-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93b29-104">語法</span><span class="sxs-lookup"><span data-stu-id="93b29-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="93b29-105">Members</span><span class="sxs-lookup"><span data-stu-id="93b29-105">Members</span></span>  
  
|<span data-ttu-id="93b29-106">成員</span><span class="sxs-lookup"><span data-stu-id="93b29-106">Member</span></span>|<span data-ttu-id="93b29-107">描述</span><span class="sxs-lookup"><span data-stu-id="93b29-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="93b29-108">指定封鎖其他 `EApiCategories` 欄位所涵蓋的所有 managed 類別和成員，使其無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="93b29-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="93b29-109">指定允許建立、操作和終結外部進程的 managed 類別和成員，無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="93b29-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="93b29-110">指定允許建立、操作和終結外部執行緒的 managed 類別和成員，無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="93b29-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="93b29-111">指定封鎖在部分信任程式碼中執行的 managed 類型和成員可能會在中止時遺漏記憶體。</span><span class="sxs-lookup"><span data-stu-id="93b29-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="93b29-112">指定不封鎖 managed 程式碼分類，使其無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="93b29-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="93b29-113">指定禁止部分信任程式碼使用 common language runtime （CLR）安全性基礎結構。</span><span class="sxs-lookup"><span data-stu-id="93b29-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="93b29-114">指定受管理的類別和成員的功能可能會影響裝載的進程，使其無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="93b29-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="93b29-115">指定受管理的類別和成員，其功能可能會影響裝載進程中的執行緒，而無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="93b29-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="93b29-116">指定會封鎖公開共用狀態的 managed 類別和成員，使其無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="93b29-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="93b29-117">指定允許使用者程式碼保留鎖定的通用語言執行平臺類別和成員，無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="93b29-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="93b29-118">指定允許或要求人為互動的 managed 類別和成員，無法在部分信任的程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="93b29-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93b29-119">備註</span><span class="sxs-lookup"><span data-stu-id="93b29-119">Remarks</span></span>  
 <span data-ttu-id="93b29-120">[ICLRHostProtectionManager：： SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)方法會接受 `EApiCategories`類型的參數。</span><span class="sxs-lookup"><span data-stu-id="93b29-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="93b29-121">`EApiCategories` 列舉和 `SetProtectedCategories` 方法與 managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> 類別直接相關。</span><span class="sxs-lookup"><span data-stu-id="93b29-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="93b29-122">Managed 類別會與 <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> 列舉搭配使用，其值會直接對應至 `EApiCategories` 值，以標示 managed 類型和成員，其會公開與 `EApiCategories`所描述之分類對應的功能。</span><span class="sxs-lookup"><span data-stu-id="93b29-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93b29-123">需求</span><span class="sxs-lookup"><span data-stu-id="93b29-123">Requirements</span></span>  
 <span data-ttu-id="93b29-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93b29-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93b29-125">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="93b29-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93b29-126">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="93b29-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93b29-127">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93b29-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b29-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="93b29-128">See also</span></span>

- [<span data-ttu-id="93b29-129">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="93b29-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="93b29-130">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="93b29-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
