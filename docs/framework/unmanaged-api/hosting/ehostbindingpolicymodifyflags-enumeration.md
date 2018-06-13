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
ms.openlocfilehash: 2fa8cc15f77ff59e3d3c570341d9bba70cf1e953
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431710"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="145c3-102">EHostBindingPolicyModifyFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="145c3-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="145c3-103">可讓主機指定的重新導向時套用至目標組件的原則修改從來源組件，應執行 common language runtime (CLR) 類型。</span><span class="sxs-lookup"><span data-stu-id="145c3-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="145c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="145c3-104">Syntax</span></span>  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="145c3-105">成員</span><span class="sxs-lookup"><span data-stu-id="145c3-105">Members</span></span>  
  
|<span data-ttu-id="145c3-106">成員</span><span class="sxs-lookup"><span data-stu-id="145c3-106">Member</span></span>|<span data-ttu-id="145c3-107">描述</span><span class="sxs-lookup"><span data-stu-id="145c3-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="145c3-108">指定 CLR 會鏈結到目標組件的來源組件的原則值。</span><span class="sxs-lookup"><span data-stu-id="145c3-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="145c3-109">指定 CLR 會執行預設動作。</span><span class="sxs-lookup"><span data-stu-id="145c3-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="145c3-110">指定 CLR 會設定為最大值的目標組件的原則值。</span><span class="sxs-lookup"><span data-stu-id="145c3-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="145c3-111">指定 CLR 會取代目標組件的原則值的來源組件。</span><span class="sxs-lookup"><span data-stu-id="145c3-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="145c3-112">備註</span><span class="sxs-lookup"><span data-stu-id="145c3-112">Remarks</span></span>  
 <span data-ttu-id="145c3-113">[Iclrhostbindingpolicymanager:: Modifyapplicationpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)方法使用的型別參數`EHostBindingPolicyModifyFlags`。</span><span class="sxs-lookup"><span data-stu-id="145c3-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="145c3-114">需求</span><span class="sxs-lookup"><span data-stu-id="145c3-114">Requirements</span></span>  
 <span data-ttu-id="145c3-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="145c3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="145c3-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="145c3-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="145c3-117">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="145c3-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="145c3-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="145c3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="145c3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="145c3-119">See Also</span></span>  
 [<span data-ttu-id="145c3-120">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="145c3-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="145c3-121">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="145c3-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
