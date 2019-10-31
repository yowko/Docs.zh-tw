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
ms.openlocfilehash: e1459c1604f3f8f043fd9b61533235ab7861c910
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120553"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="b36c9-102">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b36c9-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="b36c9-103">提供的方法可讓主機使用通用語言執行時間（CLR）內部的元件身分識別資訊來取得元件的探查識別，而不需要建立或瞭解該身分識別。</span><span class="sxs-lookup"><span data-stu-id="b36c9-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b36c9-104">方法</span><span class="sxs-lookup"><span data-stu-id="b36c9-104">Methods</span></span>  
  
|<span data-ttu-id="b36c9-105">方法</span><span class="sxs-lookup"><span data-stu-id="b36c9-105">Method</span></span>|<span data-ttu-id="b36c9-106">描述</span><span class="sxs-lookup"><span data-stu-id="b36c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b36c9-107">Get 方法</span><span class="sxs-lookup"><span data-stu-id="b36c9-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="b36c9-108">取得指定索引處的元件識別。</span><span class="sxs-lookup"><span data-stu-id="b36c9-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b36c9-109">備註</span><span class="sxs-lookup"><span data-stu-id="b36c9-109">Remarks</span></span>  
 <span data-ttu-id="b36c9-110">[ICLRAssemblyIdentityManager：： GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)之類的方法會傳回 `ICLRProbingAssemblyEnum` 實例。</span><span class="sxs-lookup"><span data-stu-id="b36c9-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b36c9-111">需求</span><span class="sxs-lookup"><span data-stu-id="b36c9-111">Requirements</span></span>  
 <span data-ttu-id="b36c9-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b36c9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b36c9-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b36c9-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b36c9-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b36c9-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b36c9-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b36c9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b36c9-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b36c9-116">See also</span></span>

- [<span data-ttu-id="b36c9-117">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="b36c9-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b36c9-118">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="b36c9-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b36c9-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="b36c9-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
