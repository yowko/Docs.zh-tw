---
title: ICLRHostBindingPolicyManager 介面
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e494bbbd08a77329b7b64816216e4bb2e1b724a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074192"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="01d15-102">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="01d15-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="01d15-103">提供方法來評估目前的繫結原則，並針對指定的組件通訊原則變更的主機。</span><span class="sxs-lookup"><span data-stu-id="01d15-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01d15-104">方法</span><span class="sxs-lookup"><span data-stu-id="01d15-104">Methods</span></span>  
  
|<span data-ttu-id="01d15-105">方法</span><span class="sxs-lookup"><span data-stu-id="01d15-105">Method</span></span>|<span data-ttu-id="01d15-106">描述</span><span class="sxs-lookup"><span data-stu-id="01d15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01d15-107">EvaluatePolicy 方法</span><span class="sxs-lookup"><span data-stu-id="01d15-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="01d15-108">代表主應用程式，會評估繫結原則。</span><span class="sxs-lookup"><span data-stu-id="01d15-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="01d15-109">ModifyApplicationPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="01d15-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="01d15-110">指定之組件，會修改繫結原則，並建立原則的新版本。</span><span class="sxs-lookup"><span data-stu-id="01d15-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01d15-111">需求</span><span class="sxs-lookup"><span data-stu-id="01d15-111">Requirements</span></span>  
 <span data-ttu-id="01d15-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01d15-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01d15-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="01d15-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01d15-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="01d15-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01d15-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01d15-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d15-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01d15-116">See also</span></span>

- [<span data-ttu-id="01d15-117">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="01d15-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="01d15-118">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="01d15-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="01d15-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="01d15-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
