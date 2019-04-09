---
title: IGCHost::Collect 方法
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdacb454783cfb8f90ea5a73807f0a199e16475d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154774"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="b2a39-102">IGCHost::Collect 方法</span><span class="sxs-lookup"><span data-stu-id="b2a39-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="b2a39-103">強制發生指定的層代，不論目前的記憶體回收集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="b2a39-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2a39-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2a39-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2a39-105">參數</span><span class="sxs-lookup"><span data-stu-id="b2a39-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="b2a39-106">[in]要執行記憶體回收層代。</span><span class="sxs-lookup"><span data-stu-id="b2a39-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="b2a39-107">-1 值表示所有層代將會進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b2a39-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2a39-108">需求</span><span class="sxs-lookup"><span data-stu-id="b2a39-108">Requirements</span></span>  
 <span data-ttu-id="b2a39-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2a39-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2a39-110">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="b2a39-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="b2a39-111">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b2a39-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b2a39-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b2a39-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b2a39-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2a39-113">See also</span></span>

- [<span data-ttu-id="b2a39-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="b2a39-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
