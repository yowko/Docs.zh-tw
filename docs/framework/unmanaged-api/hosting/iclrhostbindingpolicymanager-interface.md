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
ms.openlocfilehash: 49d1ee4dd0965d4ae5b54b53208809cfbdf7e718
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725622"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="28701-102">ICLRHostBindingPolicyManager 介面</span><span class="sxs-lookup"><span data-stu-id="28701-102">ICLRHostBindingPolicyManager Interface</span></span>

<span data-ttu-id="28701-103">提供方法，讓主機評估目前的系結原則，並針對指定的元件傳達原則變更。</span><span class="sxs-lookup"><span data-stu-id="28701-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28701-104">方法</span><span class="sxs-lookup"><span data-stu-id="28701-104">Methods</span></span>  
  
|<span data-ttu-id="28701-105">方法</span><span class="sxs-lookup"><span data-stu-id="28701-105">Method</span></span>|<span data-ttu-id="28701-106">描述</span><span class="sxs-lookup"><span data-stu-id="28701-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28701-107">EvaluatePolicy 方法</span><span class="sxs-lookup"><span data-stu-id="28701-107">EvaluatePolicy Method</span></span>](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="28701-108">代表主機評估系結原則。</span><span class="sxs-lookup"><span data-stu-id="28701-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="28701-109">ModifyApplicationPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="28701-109">ModifyApplicationPolicy Method</span></span>](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="28701-110">修改指定之元件的系結原則，並建立新的原則版本。</span><span class="sxs-lookup"><span data-stu-id="28701-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28701-111">需求</span><span class="sxs-lookup"><span data-stu-id="28701-111">Requirements</span></span>  

 <span data-ttu-id="28701-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28701-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28701-113">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="28701-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28701-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="28701-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28701-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28701-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28701-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28701-116">See also</span></span>

- [<span data-ttu-id="28701-117">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="28701-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="28701-118">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="28701-118">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="28701-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="28701-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
