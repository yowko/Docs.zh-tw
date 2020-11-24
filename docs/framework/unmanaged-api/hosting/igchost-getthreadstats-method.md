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
ms.openlocfilehash: c48b580e632d67db5a9826c210415adab1bdba96
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670065"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="130b7-102">IGCHost::GetThreadStats 方法</span><span class="sxs-lookup"><span data-stu-id="130b7-102">IGCHost::GetThreadStats Method</span></span>

<span data-ttu-id="130b7-103">取得垃圾收集的每個執行緒統計資料。</span><span class="sxs-lookup"><span data-stu-id="130b7-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="130b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="130b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="130b7-105">參數</span><span class="sxs-lookup"><span data-stu-id="130b7-105">Parameters</span></span>  

 `pFiberCookie`  
 <span data-ttu-id="130b7-106">在指定要取得其統計資料之執行緒的光纖 cookie 指標。</span><span class="sxs-lookup"><span data-stu-id="130b7-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="130b7-107">[in，out] [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) 結構的指標，其中包含指定執行緒的垃圾收集統計資料。</span><span class="sxs-lookup"><span data-stu-id="130b7-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="130b7-108">需求</span><span class="sxs-lookup"><span data-stu-id="130b7-108">Requirements</span></span>  

 <span data-ttu-id="130b7-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="130b7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="130b7-110">**標頭：** GCHost .idl、GCHost。h</span><span class="sxs-lookup"><span data-stu-id="130b7-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="130b7-111">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="130b7-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="130b7-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="130b7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130b7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="130b7-113">See also</span></span>

- [<span data-ttu-id="130b7-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="130b7-114">IGCHost Interface</span></span>](igchost-interface.md)
