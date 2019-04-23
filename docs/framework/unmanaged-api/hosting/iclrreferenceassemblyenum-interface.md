---
title: ICLRReferenceAssemblyEnum 介面
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum
helpviewer_keywords:
- ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: 8adbf092-c3ba-4bee-b25b-0de6e43a4ce5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32f27d6c15a99282eee20d2563a4ca741238d846
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187394"
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="326b0-102">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="326b0-102">ICLRReferenceAssemblyEnum Interface</span></span>
<span data-ttu-id="326b0-103">提供方法，可讓主應用程式管理的檔案或使用組件身分識別資料，而不需要建立，或了解這些身分識別的 common language runtime (CLR)、 內部資料流所參考的組件集。</span><span class="sxs-lookup"><span data-stu-id="326b0-103">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="326b0-104">方法</span><span class="sxs-lookup"><span data-stu-id="326b0-104">Methods</span></span>  
  
|<span data-ttu-id="326b0-105">方法</span><span class="sxs-lookup"><span data-stu-id="326b0-105">Method</span></span>|<span data-ttu-id="326b0-106">描述</span><span class="sxs-lookup"><span data-stu-id="326b0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="326b0-107">Get 方法</span><span class="sxs-lookup"><span data-stu-id="326b0-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="326b0-108">提供的索引處取得組件識別。</span><span class="sxs-lookup"><span data-stu-id="326b0-108">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="326b0-109">需求</span><span class="sxs-lookup"><span data-stu-id="326b0-109">Requirements</span></span>  
 <span data-ttu-id="326b0-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="326b0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="326b0-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="326b0-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="326b0-112">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="326b0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="326b0-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="326b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="326b0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="326b0-114">See also</span></span>

- [<span data-ttu-id="326b0-115">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="326b0-115">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="326b0-116">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="326b0-116">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="326b0-117">裝載介面</span><span class="sxs-lookup"><span data-stu-id="326b0-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
