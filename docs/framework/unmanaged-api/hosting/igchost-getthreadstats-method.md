---
title: IGCHost::GetThreadStats 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f86385ba4f4186d14994a2028ee11c42127546
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108341"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="b4707-102">IGCHost::GetThreadStats 方法</span><span class="sxs-lookup"><span data-stu-id="b4707-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="b4707-103">取得每個執行緒統計資料進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="b4707-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4707-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4707-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4707-105">參數</span><span class="sxs-lookup"><span data-stu-id="b4707-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="b4707-106">[in]Fiber cookie，指定要擷取的統計資料的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="b4707-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="b4707-107">[in、 out]指標[COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)結構，其中包含指定的執行緒的記憶體回收集合統計資料。</span><span class="sxs-lookup"><span data-stu-id="b4707-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4707-108">需求</span><span class="sxs-lookup"><span data-stu-id="b4707-108">Requirements</span></span>  
 <span data-ttu-id="b4707-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4707-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4707-110">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="b4707-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="b4707-111">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b4707-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4707-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4707-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4707-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4707-113">See also</span></span>

- [<span data-ttu-id="b4707-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="b4707-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
