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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e8357d20edba993f5a7682f31c04afea4362afd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796054"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="61c8a-102">EHostBindingPolicyModifyFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="61c8a-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="61c8a-103">可讓主應用程式指定的重新導向套用原則的修改從來源組件的目標組件時，應該執行 common language runtime (CLR) 型別。</span><span class="sxs-lookup"><span data-stu-id="61c8a-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61c8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="61c8a-104">Syntax</span></span>  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="61c8a-105">成員</span><span class="sxs-lookup"><span data-stu-id="61c8a-105">Members</span></span>  
  
|<span data-ttu-id="61c8a-106">成員</span><span class="sxs-lookup"><span data-stu-id="61c8a-106">Member</span></span>|<span data-ttu-id="61c8a-107">描述</span><span class="sxs-lookup"><span data-stu-id="61c8a-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="61c8a-108">指定 CLR 會鏈結至目標組件的來源組件的原則值。</span><span class="sxs-lookup"><span data-stu-id="61c8a-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="61c8a-109">指定 CLR 會執行預設動作。</span><span class="sxs-lookup"><span data-stu-id="61c8a-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="61c8a-110">指定 CLR 會設定此原則的值之目標組件的最大值。</span><span class="sxs-lookup"><span data-stu-id="61c8a-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="61c8a-111">指定 CLR 將會取代之目標組件的原則值，與來源組件。</span><span class="sxs-lookup"><span data-stu-id="61c8a-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61c8a-112">備註</span><span class="sxs-lookup"><span data-stu-id="61c8a-112">Remarks</span></span>  
 <span data-ttu-id="61c8a-113">[Iclrhostbindingpolicymanager:: Modifyapplicationpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)方法會採用類型參數的`EHostBindingPolicyModifyFlags`。</span><span class="sxs-lookup"><span data-stu-id="61c8a-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61c8a-114">需求</span><span class="sxs-lookup"><span data-stu-id="61c8a-114">Requirements</span></span>  
 <span data-ttu-id="61c8a-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61c8a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61c8a-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="61c8a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61c8a-117">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61c8a-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61c8a-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61c8a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c8a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61c8a-119">See also</span></span>

- [<span data-ttu-id="61c8a-120">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="61c8a-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="61c8a-121">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="61c8a-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
