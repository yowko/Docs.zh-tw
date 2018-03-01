---
title: "IGCHost::GetThreadStats 方法"
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
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe84dd4d231bacba6792836844058b7256124db5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="9f38c-102">IGCHost::GetThreadStats 方法</span><span class="sxs-lookup"><span data-stu-id="9f38c-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="9f38c-103">取得每個執行緒統計資料記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="9f38c-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f38c-104">語法</span><span class="sxs-lookup"><span data-stu-id="9f38c-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f38c-105">參數</span><span class="sxs-lookup"><span data-stu-id="9f38c-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="9f38c-106">[in]指定要擷取統計資料的執行緒 fiber cookie 指標。</span><span class="sxs-lookup"><span data-stu-id="9f38c-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="9f38c-107">[in、 out]指標[COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)結構，其中包含指定之執行緒的記憶體回收集合統計資料。</span><span class="sxs-lookup"><span data-stu-id="9f38c-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f38c-108">需求</span><span class="sxs-lookup"><span data-stu-id="9f38c-108">Requirements</span></span>  
 <span data-ttu-id="9f38c-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9f38c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f38c-110">**標頭：** GCHost.idl、 GCHost.h</span><span class="sxs-lookup"><span data-stu-id="9f38c-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="9f38c-111">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9f38c-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f38c-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f38c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f38c-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="9f38c-113">See Also</span></span>  
 [<span data-ttu-id="9f38c-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="9f38c-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
