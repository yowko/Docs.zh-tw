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
ms.openlocfilehash: 9797c419251127ef07a8c2bee22132c3c2b82e36
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703326"
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="63fd1-102">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="63fd1-102">ICLRReferenceAssemblyEnum Interface</span></span>
<span data-ttu-id="63fd1-103">提供的方法可讓主機使用 common language runtime （CLR）內部的元件識別資料來操作檔案或資料流程所參考的元件集，而不需要建立或瞭解這些身分識別。</span><span class="sxs-lookup"><span data-stu-id="63fd1-103">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63fd1-104">方法</span><span class="sxs-lookup"><span data-stu-id="63fd1-104">Methods</span></span>  
  
|<span data-ttu-id="63fd1-105">方法</span><span class="sxs-lookup"><span data-stu-id="63fd1-105">Method</span></span>|<span data-ttu-id="63fd1-106">描述</span><span class="sxs-lookup"><span data-stu-id="63fd1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63fd1-107">Get 方法</span><span class="sxs-lookup"><span data-stu-id="63fd1-107">Get Method</span></span>](iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="63fd1-108">取得所提供索引處的元件識別。</span><span class="sxs-lookup"><span data-stu-id="63fd1-108">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63fd1-109">需求</span><span class="sxs-lookup"><span data-stu-id="63fd1-109">Requirements</span></span>  
 <span data-ttu-id="63fd1-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63fd1-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63fd1-111">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="63fd1-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63fd1-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="63fd1-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63fd1-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63fd1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63fd1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63fd1-114">See also</span></span>

- [<span data-ttu-id="63fd1-115">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="63fd1-115">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="63fd1-116">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="63fd1-116">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="63fd1-117">裝載介面</span><span class="sxs-lookup"><span data-stu-id="63fd1-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
