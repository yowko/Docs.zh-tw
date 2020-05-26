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
ms.openlocfilehash: 4a7a2da58e197749d492f24c7a12134508efef57
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805225"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="a8ad2-102">IGCHost::GetThreadStats 方法</span><span class="sxs-lookup"><span data-stu-id="a8ad2-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="a8ad2-103">取得垃圾收集的每個執行緒統計資料。</span><span class="sxs-lookup"><span data-stu-id="a8ad2-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8ad2-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8ad2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8ad2-105">參數</span><span class="sxs-lookup"><span data-stu-id="a8ad2-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="a8ad2-106">在光纖 cookie 的指標，指定要取得其統計資料的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a8ad2-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="a8ad2-107">[in、out][COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md)結構的指標，其中包含指定之執行緒的垃圾收集統計資料。</span><span class="sxs-lookup"><span data-stu-id="a8ad2-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8ad2-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="a8ad2-108">Requirements</span></span>  
 <span data-ttu-id="a8ad2-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ad2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8ad2-110">**標頭：** GCHost .idl，GCHost。h</span><span class="sxs-lookup"><span data-stu-id="a8ad2-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="a8ad2-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a8ad2-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8ad2-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ad2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8ad2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8ad2-113">See also</span></span>

- [<span data-ttu-id="a8ad2-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="a8ad2-114">IGCHost Interface</span></span>](igchost-interface.md)
