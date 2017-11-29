---
title: "EApiCategories 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EApiCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: EApiCategories
helpviewer_keywords: EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eaff0133020fe84e58f8a130bffc8ddc2a55a19d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="a6f8b-102">EApiCategories 列舉</span><span class="sxs-lookup"><span data-stu-id="a6f8b-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="a6f8b-103">描述分類的主機可以封鎖無法在部分信任程式碼中執行的功能。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6f8b-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6f8b-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="a6f8b-105">成員</span><span class="sxs-lookup"><span data-stu-id="a6f8b-105">Members</span></span>  
  
|<span data-ttu-id="a6f8b-106">成員</span><span class="sxs-lookup"><span data-stu-id="a6f8b-106">Member</span></span>|<span data-ttu-id="a6f8b-107">說明</span><span class="sxs-lookup"><span data-stu-id="a6f8b-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="a6f8b-108">指定所有 managed 類別和成員，涵蓋的其他`EApiCategories`欄位遭到封鎖而無法在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="a6f8b-109">指定封鎖受管理的類別和成員，可讓建立、 管理和解構的外部處理序在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="a6f8b-110">指定封鎖受管理的類別和成員，可讓建立、 管理和解構的外部執行緒在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="a6f8b-111">指定封鎖無法可能遺漏記憶體中止的 managed 的類型和成員在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="a6f8b-112">指定無法在部分信任程式碼中執行封鎖的任何 managed 程式碼的類別。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="a6f8b-113">指定 common language runtime (CLR) 安全性基礎結構遭到封鎖而無法由部分信任程式碼。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="a6f8b-114">指定封鎖受管理的類別和其功能可能會影響受主控的處理序的成員在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="a6f8b-115">指定封鎖受管理的類別和其功能可能會影響裝載處理序中的執行緒的成員在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="a6f8b-116">指定封鎖受管理的類別和成員公開共用的狀態的部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="a6f8b-117">指定封鎖 common language runtime 類別和成員，可讓使用者程式碼保留鎖定在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="a6f8b-118">指定封鎖受管理的類別和成員允許或需要人為互動在部分信任程式碼中執行。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6f8b-119">備註</span><span class="sxs-lookup"><span data-stu-id="a6f8b-119">Remarks</span></span>  
 <span data-ttu-id="a6f8b-120">[Iclrhostprotectionmanager:: Setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)方法使用的型別參數`EApiCategories`。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="a6f8b-121">`EApiCategories`列舉型別和`SetProtectedCategories`方法直接相關的 managed<xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="a6f8b-122">Managed 的類別會搭配<xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>列舉型別，其值會直接對應`EApiCategories`值，將 managed 型別和成員，將功能對應至所描述的類別公開`EApiCategories`。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6f8b-123">需求</span><span class="sxs-lookup"><span data-stu-id="a6f8b-123">Requirements</span></span>  
 <span data-ttu-id="a6f8b-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6f8b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6f8b-125">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a6f8b-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6f8b-126">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6f8b-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6f8b-127">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6f8b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f8b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6f8b-128">See Also</span></span>  
 [<span data-ttu-id="a6f8b-129">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="a6f8b-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="a6f8b-130">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="a6f8b-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
