---
title: IGCHost::GetStats 方法
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9a3775f453cb432ce6b92d067f93ca54c329c06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674176"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="93535-102">IGCHost::GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="93535-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="93535-103">取得記憶體回收系統的目前狀態的統計資料。</span><span class="sxs-lookup"><span data-stu-id="93535-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93535-104">語法</span><span class="sxs-lookup"><span data-stu-id="93535-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93535-105">參數</span><span class="sxs-lookup"><span data-stu-id="93535-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="93535-106">[in、 out]指標[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)結構，包含記憶體回收系統的目前狀態的統計資料。</span><span class="sxs-lookup"><span data-stu-id="93535-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93535-107">備註</span><span class="sxs-lookup"><span data-stu-id="93535-107">Remarks</span></span>  
 <span data-ttu-id="93535-108">統計資料可以供智慧型配置系統，以協助記憶體回收系統運作。</span><span class="sxs-lookup"><span data-stu-id="93535-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="93535-109">例如，配置系統可能會決定，檢閱需要新增更多的記憶體，或強制的統計資料之後。</span><span class="sxs-lookup"><span data-stu-id="93535-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93535-110">需求</span><span class="sxs-lookup"><span data-stu-id="93535-110">Requirements</span></span>  
 <span data-ttu-id="93535-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93535-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93535-112">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="93535-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="93535-113">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="93535-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93535-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93535-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93535-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93535-115">See also</span></span>
- [<span data-ttu-id="93535-116">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="93535-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
