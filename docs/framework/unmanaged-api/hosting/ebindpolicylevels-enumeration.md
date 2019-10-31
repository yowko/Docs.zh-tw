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
ms.openlocfilehash: 81aef6beb9ee6d622519738d24fdd0a4d42a75b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136556"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="87d73-102">EBindPolicyLevels 列舉</span><span class="sxs-lookup"><span data-stu-id="87d73-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="87d73-103">提供旗標，以指定要套用或修改元件原則的層級。</span><span class="sxs-lookup"><span data-stu-id="87d73-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87d73-104">語法</span><span class="sxs-lookup"><span data-stu-id="87d73-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="87d73-105">Members</span><span class="sxs-lookup"><span data-stu-id="87d73-105">Members</span></span>  
  
|<span data-ttu-id="87d73-106">成員</span><span class="sxs-lookup"><span data-stu-id="87d73-106">Member</span></span>|<span data-ttu-id="87d73-107">描述</span><span class="sxs-lookup"><span data-stu-id="87d73-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="87d73-108">指定應該在系統管理員層級套用原則。</span><span class="sxs-lookup"><span data-stu-id="87d73-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="87d73-109">指定應該在應用層級套用原則。</span><span class="sxs-lookup"><span data-stu-id="87d73-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="87d73-110">指定應該在主機層級套用原則。</span><span class="sxs-lookup"><span data-stu-id="87d73-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="87d73-111">不指定原則層級旗標。</span><span class="sxs-lookup"><span data-stu-id="87d73-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="87d73-112">指定應該在發行者層級套用原則。</span><span class="sxs-lookup"><span data-stu-id="87d73-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="87d73-113">指定原則應該適用于變數層級。</span><span class="sxs-lookup"><span data-stu-id="87d73-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="87d73-114">指定原則應該支援 .NET Framework 元件的執行之間的可攜性。</span><span class="sxs-lookup"><span data-stu-id="87d73-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="87d73-115">請參閱[\<supportportability> >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)設定檔元素。</span><span class="sxs-lookup"><span data-stu-id="87d73-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="87d73-116">指定應該與 common language runtime （CLR）的原則一致。</span><span class="sxs-lookup"><span data-stu-id="87d73-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87d73-117">備註</span><span class="sxs-lookup"><span data-stu-id="87d73-117">Remarks</span></span>  
 <span data-ttu-id="87d73-118">此列舉會傳遞給[ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)介面的方法，以指定應用程式原則中的變更。</span><span class="sxs-lookup"><span data-stu-id="87d73-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87d73-119">需求</span><span class="sxs-lookup"><span data-stu-id="87d73-119">Requirements</span></span>  
 <span data-ttu-id="87d73-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87d73-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87d73-121">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="87d73-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87d73-122">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="87d73-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87d73-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87d73-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d73-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="87d73-124">See also</span></span>

- [<span data-ttu-id="87d73-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="87d73-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="87d73-126">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="87d73-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
