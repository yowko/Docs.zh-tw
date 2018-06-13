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
ms.openlocfilehash: 74827fac102ee6045965f4ba9d74dd3b1aa0af86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437566"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="c4a85-102">IGCHost::GetThreadStats 方法</span><span class="sxs-lookup"><span data-stu-id="c4a85-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="c4a85-103">取得每個執行緒統計資料記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="c4a85-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a85-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4a85-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4a85-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4a85-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="c4a85-106">[in]指定要擷取統計資料的執行緒 fiber cookie 指標。</span><span class="sxs-lookup"><span data-stu-id="c4a85-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="c4a85-107">[in、 out]指標[COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)結構，其中包含指定之執行緒的記憶體回收集合統計資料。</span><span class="sxs-lookup"><span data-stu-id="c4a85-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4a85-108">需求</span><span class="sxs-lookup"><span data-stu-id="c4a85-108">Requirements</span></span>  
 <span data-ttu-id="c4a85-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4a85-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4a85-110">**標頭：** GCHost.idl、 GCHost.h</span><span class="sxs-lookup"><span data-stu-id="c4a85-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="c4a85-111">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c4a85-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4a85-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4a85-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a85-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4a85-113">See Also</span></span>  
 [<span data-ttu-id="c4a85-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="c4a85-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
