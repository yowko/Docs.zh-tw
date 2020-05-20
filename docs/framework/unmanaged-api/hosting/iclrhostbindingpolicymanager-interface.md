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
ms.openlocfilehash: 3cf2a945607bf85a51dbec35342ff5ac46878bca
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703576"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="66419-102">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="66419-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="66419-103">提供方法，讓主機評估目前的系結原則，並傳達指定元件的原則變更。</span><span class="sxs-lookup"><span data-stu-id="66419-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66419-104">方法</span><span class="sxs-lookup"><span data-stu-id="66419-104">Methods</span></span>  
  
|<span data-ttu-id="66419-105">方法</span><span class="sxs-lookup"><span data-stu-id="66419-105">Method</span></span>|<span data-ttu-id="66419-106">描述</span><span class="sxs-lookup"><span data-stu-id="66419-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66419-107">EvaluatePolicy 方法</span><span class="sxs-lookup"><span data-stu-id="66419-107">EvaluatePolicy Method</span></span>](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="66419-108">代表主機評估系結原則。</span><span class="sxs-lookup"><span data-stu-id="66419-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="66419-109">ModifyApplicationPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="66419-109">ModifyApplicationPolicy Method</span></span>](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="66419-110">修改指定元件的系結原則，並建立新版本的原則。</span><span class="sxs-lookup"><span data-stu-id="66419-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66419-111">需求</span><span class="sxs-lookup"><span data-stu-id="66419-111">Requirements</span></span>  
 <span data-ttu-id="66419-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="66419-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66419-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="66419-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66419-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="66419-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66419-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66419-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66419-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66419-116">See also</span></span>

- [<span data-ttu-id="66419-117">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="66419-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="66419-118">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="66419-118">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="66419-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="66419-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
