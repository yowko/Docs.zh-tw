---
title: "ICLRReferenceAssemblyEnum 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRReferenceAssemblyEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRReferenceAssemblyEnum
helpviewer_keywords: ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: 8adbf092-c3ba-4bee-b25b-0de6e43a4ce5
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7d2a295c4c35761d0a47e1690cd7b88387cecdb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="f5252-102">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="f5252-102">ICLRReferenceAssemblyEnum Interface</span></span>
<span data-ttu-id="f5252-103">提供方法，讓主應用程式管理的檔案或使用組件識別資料，而不需要建立，或了解這些識別的 common language runtime (CLR)，內部資料流所參考的組件集。</span><span class="sxs-lookup"><span data-stu-id="f5252-103">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5252-104">方法</span><span class="sxs-lookup"><span data-stu-id="f5252-104">Methods</span></span>  
  
|<span data-ttu-id="f5252-105">方法</span><span class="sxs-lookup"><span data-stu-id="f5252-105">Method</span></span>|<span data-ttu-id="f5252-106">描述</span><span class="sxs-lookup"><span data-stu-id="f5252-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5252-107">Get 方法</span><span class="sxs-lookup"><span data-stu-id="f5252-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="f5252-108">在提供的索引取得組件識別。</span><span class="sxs-lookup"><span data-stu-id="f5252-108">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5252-109">需求</span><span class="sxs-lookup"><span data-stu-id="f5252-109">Requirements</span></span>  
 <span data-ttu-id="f5252-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5252-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5252-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5252-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5252-112">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f5252-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5252-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5252-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5252-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="f5252-114">See Also</span></span>  
 [<span data-ttu-id="f5252-115">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="f5252-115">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="f5252-116">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="f5252-116">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="f5252-117">裝載介面</span><span class="sxs-lookup"><span data-stu-id="f5252-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
