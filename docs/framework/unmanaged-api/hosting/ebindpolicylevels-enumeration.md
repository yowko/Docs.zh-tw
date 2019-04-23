---
title: EBindPolicyLevels 列舉
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8f2b08662e719a3308a62ab5b60f5dc490f2a6a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142203"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="507f4-102">EBindPolicyLevels 列舉</span><span class="sxs-lookup"><span data-stu-id="507f4-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="507f4-103">提供旗標指定要套用或修改的組件原則的層級。</span><span class="sxs-lookup"><span data-stu-id="507f4-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="507f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="507f4-104">Syntax</span></span>  
  
```  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a><span data-ttu-id="507f4-105">成員</span><span class="sxs-lookup"><span data-stu-id="507f4-105">Members</span></span>  
  
|<span data-ttu-id="507f4-106">成員</span><span class="sxs-lookup"><span data-stu-id="507f4-106">Member</span></span>|<span data-ttu-id="507f4-107">描述</span><span class="sxs-lookup"><span data-stu-id="507f4-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="507f4-108">指定原則應該套用系統管理員層級。</span><span class="sxs-lookup"><span data-stu-id="507f4-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="507f4-109">指定原則應該套用應用程式層級。</span><span class="sxs-lookup"><span data-stu-id="507f4-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="507f4-110">指定原則應該套用在主機層級。</span><span class="sxs-lookup"><span data-stu-id="507f4-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="507f4-111">不指定原則層級旗標。</span><span class="sxs-lookup"><span data-stu-id="507f4-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="507f4-112">指定原則應該套用在發行者層級。</span><span class="sxs-lookup"><span data-stu-id="507f4-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="507f4-113">指定變數的層級應該是適用原則。</span><span class="sxs-lookup"><span data-stu-id="507f4-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="507f4-114">指定原則應該支援的.NET Framework 組件實作之間的可攜性。</span><span class="sxs-lookup"><span data-stu-id="507f4-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="507f4-115">請參閱[ \<Supportportability> >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)組態檔項目。</span><span class="sxs-lookup"><span data-stu-id="507f4-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="507f4-116">指定原則應該進行整合的 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="507f4-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="507f4-117">備註</span><span class="sxs-lookup"><span data-stu-id="507f4-117">Remarks</span></span>  
 <span data-ttu-id="507f4-118">此列舉會傳遞至方法[ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)介面來指定應用程式原則中的變更。</span><span class="sxs-lookup"><span data-stu-id="507f4-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="507f4-119">需求</span><span class="sxs-lookup"><span data-stu-id="507f4-119">Requirements</span></span>  
 <span data-ttu-id="507f4-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="507f4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="507f4-121">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="507f4-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="507f4-122">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="507f4-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="507f4-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="507f4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="507f4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="507f4-124">See also</span></span>

- [<span data-ttu-id="507f4-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="507f4-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="507f4-126">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="507f4-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
