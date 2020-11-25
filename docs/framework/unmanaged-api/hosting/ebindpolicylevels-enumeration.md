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
ms.openlocfilehash: a0992ca8ac4bfffef681c74de455a0eeb627a042
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726843"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="34888-102">EBindPolicyLevels 列舉</span><span class="sxs-lookup"><span data-stu-id="34888-102">EBindPolicyLevels Enumeration</span></span>

<span data-ttu-id="34888-103">提供旗標來指定要套用或修改元件原則的層級。</span><span class="sxs-lookup"><span data-stu-id="34888-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34888-104">語法</span><span class="sxs-lookup"><span data-stu-id="34888-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="34888-105">成員</span><span class="sxs-lookup"><span data-stu-id="34888-105">Members</span></span>  
  
|<span data-ttu-id="34888-106">member</span><span class="sxs-lookup"><span data-stu-id="34888-106">Member</span></span>|<span data-ttu-id="34888-107">描述</span><span class="sxs-lookup"><span data-stu-id="34888-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="34888-108">指定應在系統管理員層級套用原則。</span><span class="sxs-lookup"><span data-stu-id="34888-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="34888-109">指定應在應用層級套用原則。</span><span class="sxs-lookup"><span data-stu-id="34888-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="34888-110">指定應在主機層級套用原則。</span><span class="sxs-lookup"><span data-stu-id="34888-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="34888-111">未指定原則層級旗標。</span><span class="sxs-lookup"><span data-stu-id="34888-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="34888-112">指定應在發行者層級套用原則。</span><span class="sxs-lookup"><span data-stu-id="34888-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="34888-113">指定原則應該適用于變數層級。</span><span class="sxs-lookup"><span data-stu-id="34888-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="34888-114">指定原則應該支援 .NET Framework 元件的執行之間的可攜性。</span><span class="sxs-lookup"><span data-stu-id="34888-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="34888-115">請參閱 [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) 設定檔元素。</span><span class="sxs-lookup"><span data-stu-id="34888-115">See the [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="34888-116">指定原則應該與 common language runtime (CLR) 整合。</span><span class="sxs-lookup"><span data-stu-id="34888-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34888-117">備註</span><span class="sxs-lookup"><span data-stu-id="34888-117">Remarks</span></span>  

 <span data-ttu-id="34888-118">此列舉會傳遞給 [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) 介面的方法，以指定應用程式原則的變更。</span><span class="sxs-lookup"><span data-stu-id="34888-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34888-119">需求</span><span class="sxs-lookup"><span data-stu-id="34888-119">Requirements</span></span>  

 <span data-ttu-id="34888-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34888-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34888-121">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="34888-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34888-122">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34888-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34888-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34888-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34888-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34888-124">See also</span></span>

- [<span data-ttu-id="34888-125">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="34888-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="34888-126">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="34888-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
