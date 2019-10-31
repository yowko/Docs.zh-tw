---
title: COR_GC_THREAD_STATS_TYPES 列舉
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS_TYPES
helpviewer_keywords:
- COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type:
- apiref
ms.openlocfilehash: 63275aaa7ed1f63c4f100845d2cbe9e93fcd0bcd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131248"
---
# <a name="cor_gc_thread_stats_types-enumeration"></a><span data-ttu-id="985e6-102">COR_GC_THREAD_STATS_TYPES 列舉</span><span class="sxs-lookup"><span data-stu-id="985e6-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="985e6-103">表示執行緒的垃圾收集統計資料。</span><span class="sxs-lookup"><span data-stu-id="985e6-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="985e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="985e6-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="985e6-105">Members</span><span class="sxs-lookup"><span data-stu-id="985e6-105">Members</span></span>  
  
|<span data-ttu-id="985e6-106">成員</span><span class="sxs-lookup"><span data-stu-id="985e6-106">Member</span></span>|<span data-ttu-id="985e6-107">描述</span><span class="sxs-lookup"><span data-stu-id="985e6-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="985e6-108">執行緒具有在最近一次垃圾收集中升級的位元組數。</span><span class="sxs-lookup"><span data-stu-id="985e6-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="985e6-109">需求</span><span class="sxs-lookup"><span data-stu-id="985e6-109">Requirements</span></span>  
 <span data-ttu-id="985e6-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="985e6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="985e6-111">**標頭：** GCHost .idl，GCHost。h</span><span class="sxs-lookup"><span data-stu-id="985e6-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="985e6-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="985e6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="985e6-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="985e6-113">See also</span></span>

- [<span data-ttu-id="985e6-114">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="985e6-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
