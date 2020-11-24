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
ms.openlocfilehash: 189fbb1943d049dc4f52ea6cb626c02e9e25b3c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686134"
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="d737a-102">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="d737a-102">ICLRReferenceAssemblyEnum Interface</span></span>

<span data-ttu-id="d737a-103">提供的方法可讓主機使用 common language runtime (CLR) 內部的元件身分識別資料，來操作檔案或資料流程所參考的元件集合，而不需要建立或瞭解這些身分識別。</span><span class="sxs-lookup"><span data-stu-id="d737a-103">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d737a-104">方法</span><span class="sxs-lookup"><span data-stu-id="d737a-104">Methods</span></span>  
  
|<span data-ttu-id="d737a-105">方法</span><span class="sxs-lookup"><span data-stu-id="d737a-105">Method</span></span>|<span data-ttu-id="d737a-106">描述</span><span class="sxs-lookup"><span data-stu-id="d737a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d737a-107">Get 方法</span><span class="sxs-lookup"><span data-stu-id="d737a-107">Get Method</span></span>](iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="d737a-108">取得提供的索引處的元件識別。</span><span class="sxs-lookup"><span data-stu-id="d737a-108">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d737a-109">需求</span><span class="sxs-lookup"><span data-stu-id="d737a-109">Requirements</span></span>  

 <span data-ttu-id="d737a-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d737a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d737a-111">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d737a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d737a-112">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d737a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d737a-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d737a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d737a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d737a-114">See also</span></span>

- [<span data-ttu-id="d737a-115">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="d737a-115">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="d737a-116">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="d737a-116">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d737a-117">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d737a-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
