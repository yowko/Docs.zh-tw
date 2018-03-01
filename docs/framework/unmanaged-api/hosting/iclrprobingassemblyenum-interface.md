---
title: "ICLRProbingAssemblyEnum 介面"
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
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 31f3bfcb2b70bda952f0e4bb43dd8b0067e6ef1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="df93a-102">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="df93a-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="df93a-103">提供方法，讓主應用程式，以取得組件的探查識別使用的是 common language runtime (CLR)，內部，不需要建立或了解該身分識別的組件的識別資訊。</span><span class="sxs-lookup"><span data-stu-id="df93a-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df93a-104">方法</span><span class="sxs-lookup"><span data-stu-id="df93a-104">Methods</span></span>  
  
|<span data-ttu-id="df93a-105">方法</span><span class="sxs-lookup"><span data-stu-id="df93a-105">Method</span></span>|<span data-ttu-id="df93a-106">描述</span><span class="sxs-lookup"><span data-stu-id="df93a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df93a-107">Get 方法</span><span class="sxs-lookup"><span data-stu-id="df93a-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="df93a-108">取得指定索引處的組件識別。</span><span class="sxs-lookup"><span data-stu-id="df93a-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df93a-109">備註</span><span class="sxs-lookup"><span data-stu-id="df93a-109">Remarks</span></span>  
 <span data-ttu-id="df93a-110">這類方法[iclrassemblyidentitymanager:: Getprobingassembliesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)傳回`ICLRProbingAssemblyEnum`執行個體。</span><span class="sxs-lookup"><span data-stu-id="df93a-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df93a-111">需求</span><span class="sxs-lookup"><span data-stu-id="df93a-111">Requirements</span></span>  
 <span data-ttu-id="df93a-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df93a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df93a-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df93a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df93a-114">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="df93a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df93a-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df93a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df93a-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="df93a-116">See Also</span></span>  
 [<span data-ttu-id="df93a-117">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="df93a-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="df93a-118">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="df93a-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="df93a-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="df93a-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
