---
title: "ICLRHostBindingPolicyManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d2dd55268e9f54554ec3e9a9b61573b708aa5acc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="31d16-102">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="31d16-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="31d16-103">提供方法來評估目前的繫結原則，並指定組件通訊原則變更的主機。</span><span class="sxs-lookup"><span data-stu-id="31d16-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31d16-104">方法</span><span class="sxs-lookup"><span data-stu-id="31d16-104">Methods</span></span>  
  
|<span data-ttu-id="31d16-105">方法</span><span class="sxs-lookup"><span data-stu-id="31d16-105">Method</span></span>|<span data-ttu-id="31d16-106">描述</span><span class="sxs-lookup"><span data-stu-id="31d16-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31d16-107">EvaluatePolicy 方法</span><span class="sxs-lookup"><span data-stu-id="31d16-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="31d16-108">代表主機評估繫結原則。</span><span class="sxs-lookup"><span data-stu-id="31d16-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="31d16-109">ModifyApplicationPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="31d16-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="31d16-110">修改繫結原則的指定組件，並建立新的原則版本。</span><span class="sxs-lookup"><span data-stu-id="31d16-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="31d16-111">需求</span><span class="sxs-lookup"><span data-stu-id="31d16-111">Requirements</span></span>  
 <span data-ttu-id="31d16-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31d16-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31d16-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="31d16-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31d16-114">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="31d16-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31d16-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d16-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d16-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="31d16-116">See Also</span></span>  
 [<span data-ttu-id="31d16-117">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="31d16-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="31d16-118">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="31d16-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="31d16-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="31d16-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
