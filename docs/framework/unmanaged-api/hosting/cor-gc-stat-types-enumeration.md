---
title: COR_GC_STAT_TYPES 列舉
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: cca393ae34144787ab7800baec7c58209394f30e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616712"
---
# <a name="cor_gc_stat_types-enumeration"></a><span data-ttu-id="cf9e6-102">COR_GC_STAT_TYPES 列舉</span><span class="sxs-lookup"><span data-stu-id="cf9e6-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="cf9e6-103">指定要記錄以進行垃圾收集的統計資料。</span><span class="sxs-lookup"><span data-stu-id="cf9e6-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf9e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="cf9e6-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="cf9e6-105">備註</span><span class="sxs-lookup"><span data-stu-id="cf9e6-105">Remarks</span></span>  
 <span data-ttu-id="cf9e6-106">此列舉會指定要由[ICLRGCManager：： GetStats](iclrgcmanager-getstats-method.md)方法來設定[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)結構中的哪些統計資料。</span><span class="sxs-lookup"><span data-stu-id="cf9e6-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="cf9e6-107">成員</span><span class="sxs-lookup"><span data-stu-id="cf9e6-107">Members</span></span>  
  
|<span data-ttu-id="cf9e6-108">成員</span><span class="sxs-lookup"><span data-stu-id="cf9e6-108">Member</span></span>|<span data-ttu-id="cf9e6-109">說明</span><span class="sxs-lookup"><span data-stu-id="cf9e6-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="cf9e6-110">記錄每個層代所執行的垃圾收集數目。</span><span class="sxs-lookup"><span data-stu-id="cf9e6-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="cf9e6-111">記錄記憶體使用量和垃圾收集大小統計資料。</span><span class="sxs-lookup"><span data-stu-id="cf9e6-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf9e6-112">需求</span><span class="sxs-lookup"><span data-stu-id="cf9e6-112">Requirements</span></span>  
 <span data-ttu-id="cf9e6-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf9e6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf9e6-114">**標頭：** GCHost .idl，GCHost。h</span><span class="sxs-lookup"><span data-stu-id="cf9e6-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="cf9e6-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf9e6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf9e6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf9e6-116">See also</span></span>

- [<span data-ttu-id="cf9e6-117">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="cf9e6-117">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="cf9e6-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="cf9e6-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
