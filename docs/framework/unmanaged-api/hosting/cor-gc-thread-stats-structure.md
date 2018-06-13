---
title: COR_GC_THREAD_STATS 結構
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24a386fe82bbd004954924a573c090af7f58824a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431824"
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="bb9d5-102">COR_GC_THREAD_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="bb9d5-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="bb9d5-103">包含記憶體回收相關的每個執行緒統計資料。</span><span class="sxs-lookup"><span data-stu-id="bb9d5-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb9d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb9d5-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="bb9d5-105">成員</span><span class="sxs-lookup"><span data-stu-id="bb9d5-105">Members</span></span>  
  
|<span data-ttu-id="bb9d5-106">成員</span><span class="sxs-lookup"><span data-stu-id="bb9d5-106">Member</span></span>|<span data-ttu-id="bb9d5-107">描述</span><span class="sxs-lookup"><span data-stu-id="bb9d5-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="bb9d5-108">已關聯到目前的執行緒上配置的記憶體位元組數目`COR_GC_THREAD_STATS`執行個體。</span><span class="sxs-lookup"><span data-stu-id="bb9d5-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="bb9d5-109">每次層代 0 記憶體回收發生時清除這個數字為零。</span><span class="sxs-lookup"><span data-stu-id="bb9d5-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="bb9d5-110">最新的回收中升級高的層代的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="bb9d5-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb9d5-111">備註</span><span class="sxs-lookup"><span data-stu-id="bb9d5-111">Remarks</span></span>  
 <span data-ttu-id="bb9d5-112">[Iclrtask:: Getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)採用輸出參數的型別`COR_GC_THREAD_STATS`。</span><span class="sxs-lookup"><span data-stu-id="bb9d5-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb9d5-113">需求</span><span class="sxs-lookup"><span data-stu-id="bb9d5-113">Requirements</span></span>  
 <span data-ttu-id="bb9d5-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9d5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb9d5-115">**標頭：** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="bb9d5-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="bb9d5-116">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bb9d5-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb9d5-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb9d5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9d5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb9d5-118">See Also</span></span>  
 [<span data-ttu-id="bb9d5-119">裝載結構</span><span class="sxs-lookup"><span data-stu-id="bb9d5-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="bb9d5-120">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="bb9d5-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
