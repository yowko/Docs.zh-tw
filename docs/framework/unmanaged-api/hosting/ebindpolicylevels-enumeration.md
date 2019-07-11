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
ms.openlocfilehash: e61acbb15844c5ddfc8b7aa98c41bb18c6e9ade5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769768"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="21480-102">EBindPolicyLevels 列舉</span><span class="sxs-lookup"><span data-stu-id="21480-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="21480-103">提供旗標指定要套用或修改的組件原則的層級。</span><span class="sxs-lookup"><span data-stu-id="21480-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21480-104">語法</span><span class="sxs-lookup"><span data-stu-id="21480-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="21480-105">成員</span><span class="sxs-lookup"><span data-stu-id="21480-105">Members</span></span>  
  
|<span data-ttu-id="21480-106">成員</span><span class="sxs-lookup"><span data-stu-id="21480-106">Member</span></span>|<span data-ttu-id="21480-107">描述</span><span class="sxs-lookup"><span data-stu-id="21480-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="21480-108">指定原則應該套用系統管理員層級。</span><span class="sxs-lookup"><span data-stu-id="21480-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="21480-109">指定原則應該套用應用程式層級。</span><span class="sxs-lookup"><span data-stu-id="21480-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="21480-110">指定原則應該套用在主機層級。</span><span class="sxs-lookup"><span data-stu-id="21480-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="21480-111">不指定原則層級旗標。</span><span class="sxs-lookup"><span data-stu-id="21480-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="21480-112">指定原則應該套用在發行者層級。</span><span class="sxs-lookup"><span data-stu-id="21480-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="21480-113">指定變數的層級應該是適用原則。</span><span class="sxs-lookup"><span data-stu-id="21480-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="21480-114">指定原則應該支援的.NET Framework 組件實作之間的可攜性。</span><span class="sxs-lookup"><span data-stu-id="21480-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="21480-115">請參閱[ \<Supportportability> >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)組態檔項目。</span><span class="sxs-lookup"><span data-stu-id="21480-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="21480-116">指定原則應該進行整合的 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="21480-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21480-117">備註</span><span class="sxs-lookup"><span data-stu-id="21480-117">Remarks</span></span>  
 <span data-ttu-id="21480-118">此列舉會傳遞至方法[ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)介面來指定應用程式原則中的變更。</span><span class="sxs-lookup"><span data-stu-id="21480-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21480-119">需求</span><span class="sxs-lookup"><span data-stu-id="21480-119">Requirements</span></span>  
 <span data-ttu-id="21480-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21480-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21480-121">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="21480-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21480-122">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21480-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21480-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21480-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21480-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21480-124">See also</span></span>

- [<span data-ttu-id="21480-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="21480-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="21480-126">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="21480-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
