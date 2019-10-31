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
ms.openlocfilehash: 36eeb7ed4f80979ef2edb930e65963a1db0c894f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134910"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="f61d1-102">IGCHost::GetThreadStats 方法</span><span class="sxs-lookup"><span data-stu-id="f61d1-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="f61d1-103">取得垃圾收集的每個執行緒統計資料。</span><span class="sxs-lookup"><span data-stu-id="f61d1-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f61d1-104">語法</span><span class="sxs-lookup"><span data-stu-id="f61d1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f61d1-105">參數</span><span class="sxs-lookup"><span data-stu-id="f61d1-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="f61d1-106">在光纖 cookie 的指標，指定要取得其統計資料的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f61d1-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="f61d1-107">[in、out][COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)結構的指標，其中包含指定之執行緒的垃圾收集統計資料。</span><span class="sxs-lookup"><span data-stu-id="f61d1-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f61d1-108">需求</span><span class="sxs-lookup"><span data-stu-id="f61d1-108">Requirements</span></span>  
 <span data-ttu-id="f61d1-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f61d1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f61d1-110">**標頭：** GCHost .idl，GCHost。h</span><span class="sxs-lookup"><span data-stu-id="f61d1-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f61d1-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f61d1-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f61d1-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f61d1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f61d1-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="f61d1-113">See also</span></span>

- [<span data-ttu-id="f61d1-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="f61d1-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
