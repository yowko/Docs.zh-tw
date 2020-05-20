---
title: EHostBindingPolicyModifyFlags 列舉
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: 256c362ae0aea51fea16ce799db243b105dee81a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616238"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="247de-102">EHostBindingPolicyModifyFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="247de-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="247de-103">允許主機指定將原則修改從來源元件套用至目標群組件時，common language runtime （CLR）應執行的重新導向類型。</span><span class="sxs-lookup"><span data-stu-id="247de-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="247de-104">語法</span><span class="sxs-lookup"><span data-stu-id="247de-104">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="247de-105">成員</span><span class="sxs-lookup"><span data-stu-id="247de-105">Members</span></span>  
  
|<span data-ttu-id="247de-106">成員</span><span class="sxs-lookup"><span data-stu-id="247de-106">Member</span></span>|<span data-ttu-id="247de-107">說明</span><span class="sxs-lookup"><span data-stu-id="247de-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="247de-108">指定 CLR 會將來源元件的原則值鏈到目標群組件的。</span><span class="sxs-lookup"><span data-stu-id="247de-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="247de-109">指定 CLR 將會執行預設動作。</span><span class="sxs-lookup"><span data-stu-id="247de-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="247de-110">指定 CLR 將目標群組件的原則值設定為最大值。</span><span class="sxs-lookup"><span data-stu-id="247de-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="247de-111">指定 CLR 將會以來源元件的原則值取代目標群組件。</span><span class="sxs-lookup"><span data-stu-id="247de-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="247de-112">備註</span><span class="sxs-lookup"><span data-stu-id="247de-112">Remarks</span></span>  
 <span data-ttu-id="247de-113">[ICLRHostBindingPolicyManager：： ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)方法接受型別為的參數 `EHostBindingPolicyModifyFlags` 。</span><span class="sxs-lookup"><span data-stu-id="247de-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="247de-114">需求</span><span class="sxs-lookup"><span data-stu-id="247de-114">Requirements</span></span>  
 <span data-ttu-id="247de-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="247de-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="247de-116">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="247de-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="247de-117">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="247de-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="247de-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="247de-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="247de-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="247de-119">See also</span></span>

- [<span data-ttu-id="247de-120">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="247de-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="247de-121">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="247de-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
