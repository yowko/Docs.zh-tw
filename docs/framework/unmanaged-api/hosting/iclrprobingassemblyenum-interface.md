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
ms.openlocfilehash: 6df08889af30542af5a128cbffc38a57ce640fde
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728923"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="59332-102">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="59332-102">ICLRProbingAssemblyEnum Interface</span></span>

<span data-ttu-id="59332-103">提供的方法可讓主機使用 common language runtime (CLR) 內部的元件身分識別資訊，來取得元件的探查識別，而不需要建立或瞭解該身分識別。</span><span class="sxs-lookup"><span data-stu-id="59332-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59332-104">方法</span><span class="sxs-lookup"><span data-stu-id="59332-104">Methods</span></span>  
  
|<span data-ttu-id="59332-105">方法</span><span class="sxs-lookup"><span data-stu-id="59332-105">Method</span></span>|<span data-ttu-id="59332-106">描述</span><span class="sxs-lookup"><span data-stu-id="59332-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59332-107">Get 方法</span><span class="sxs-lookup"><span data-stu-id="59332-107">Get Method</span></span>](iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="59332-108">取得位於指定索引處的元件識別。</span><span class="sxs-lookup"><span data-stu-id="59332-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59332-109">備註</span><span class="sxs-lookup"><span data-stu-id="59332-109">Remarks</span></span>  

 <span data-ttu-id="59332-110">[ICLRAssemblyIdentityManager：： GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)之類的方法會傳回 `ICLRProbingAssemblyEnum` 實例。</span><span class="sxs-lookup"><span data-stu-id="59332-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59332-111">需求</span><span class="sxs-lookup"><span data-stu-id="59332-111">Requirements</span></span>  

 <span data-ttu-id="59332-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59332-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59332-113">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="59332-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59332-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="59332-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59332-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59332-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59332-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59332-116">See also</span></span>

- [<span data-ttu-id="59332-117">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="59332-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="59332-118">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="59332-118">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="59332-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="59332-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
