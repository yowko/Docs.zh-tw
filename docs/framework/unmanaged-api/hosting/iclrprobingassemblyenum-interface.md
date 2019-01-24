---
title: ICLRProbingAssemblyEnum 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d471d7a33a048315b3a7fd9107baa0ad95a865c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678768"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="837d8-102">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="837d8-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="837d8-103">提供方法，讓主應用程式，以取得組件探查的身分識別使用而不需要建立，或了解該身分識別的 common language runtime (CLR)、 內部組件的身分識別資訊。</span><span class="sxs-lookup"><span data-stu-id="837d8-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="837d8-104">方法</span><span class="sxs-lookup"><span data-stu-id="837d8-104">Methods</span></span>  
  
|<span data-ttu-id="837d8-105">方法</span><span class="sxs-lookup"><span data-stu-id="837d8-105">Method</span></span>|<span data-ttu-id="837d8-106">描述</span><span class="sxs-lookup"><span data-stu-id="837d8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="837d8-107">Get 方法</span><span class="sxs-lookup"><span data-stu-id="837d8-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="837d8-108">取得組件識別的指定索引處。</span><span class="sxs-lookup"><span data-stu-id="837d8-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="837d8-109">備註</span><span class="sxs-lookup"><span data-stu-id="837d8-109">Remarks</span></span>  
 <span data-ttu-id="837d8-110">這類方法[iclrassemblyidentitymanager:: Getprobingassembliesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)傳回`ICLRProbingAssemblyEnum`執行個體。</span><span class="sxs-lookup"><span data-stu-id="837d8-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="837d8-111">需求</span><span class="sxs-lookup"><span data-stu-id="837d8-111">Requirements</span></span>  
 <span data-ttu-id="837d8-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="837d8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="837d8-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="837d8-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="837d8-114">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="837d8-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="837d8-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="837d8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="837d8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="837d8-116">See also</span></span>
- [<span data-ttu-id="837d8-117">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="837d8-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="837d8-118">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="837d8-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="837d8-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="837d8-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
