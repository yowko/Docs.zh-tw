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
ms.openlocfilehash: 94d2ec12309249afbecdc4130f8fe20c927b0a9b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616368"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="af9de-102">EBindPolicyLevels 列舉</span><span class="sxs-lookup"><span data-stu-id="af9de-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="af9de-103">提供旗標，以指定要套用或修改元件原則的層級。</span><span class="sxs-lookup"><span data-stu-id="af9de-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af9de-104">語法</span><span class="sxs-lookup"><span data-stu-id="af9de-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="af9de-105">成員</span><span class="sxs-lookup"><span data-stu-id="af9de-105">Members</span></span>  
  
|<span data-ttu-id="af9de-106">成員</span><span class="sxs-lookup"><span data-stu-id="af9de-106">Member</span></span>|<span data-ttu-id="af9de-107">說明</span><span class="sxs-lookup"><span data-stu-id="af9de-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="af9de-108">指定應該在系統管理員層級套用原則。</span><span class="sxs-lookup"><span data-stu-id="af9de-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="af9de-109">指定應該在應用層級套用原則。</span><span class="sxs-lookup"><span data-stu-id="af9de-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="af9de-110">指定應該在主機層級套用原則。</span><span class="sxs-lookup"><span data-stu-id="af9de-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="af9de-111">不指定原則層級旗標。</span><span class="sxs-lookup"><span data-stu-id="af9de-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="af9de-112">指定應該在發行者層級套用原則。</span><span class="sxs-lookup"><span data-stu-id="af9de-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="af9de-113">指定原則應該適用于變數層級。</span><span class="sxs-lookup"><span data-stu-id="af9de-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="af9de-114">指定原則應該支援 .NET Framework 元件的執行之間的可攜性。</span><span class="sxs-lookup"><span data-stu-id="af9de-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="af9de-115">請參閱[ \< supportportability>>](../../configure-apps/file-schema/runtime/supportportability-element.md)設定檔元素。</span><span class="sxs-lookup"><span data-stu-id="af9de-115">See the [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="af9de-116">指定應該與 common language runtime （CLR）的原則一致。</span><span class="sxs-lookup"><span data-stu-id="af9de-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af9de-117">備註</span><span class="sxs-lookup"><span data-stu-id="af9de-117">Remarks</span></span>  
 <span data-ttu-id="af9de-118">此列舉會傳遞給[ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md)介面的方法，以指定應用程式原則中的變更。</span><span class="sxs-lookup"><span data-stu-id="af9de-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af9de-119">需求</span><span class="sxs-lookup"><span data-stu-id="af9de-119">Requirements</span></span>  
 <span data-ttu-id="af9de-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af9de-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af9de-121">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="af9de-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af9de-122">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="af9de-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af9de-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af9de-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af9de-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af9de-124">See also</span></span>

- [<span data-ttu-id="af9de-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="af9de-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="af9de-126">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="af9de-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
