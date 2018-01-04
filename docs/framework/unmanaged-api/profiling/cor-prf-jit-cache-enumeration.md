---
title: "COR_PRF_JIT_CACHE 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_JIT_CACHE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_JIT_CACHE
helpviewer_keywords: COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5041e12c6745d43518ee2ac45e3a0a79c1c50ca3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="4d2fe-102">COR_PRF_JIT_CACHE 列舉</span><span class="sxs-lookup"><span data-stu-id="4d2fe-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="4d2fe-103">指出快取的函式搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="4d2fe-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d2fe-104">`COR_PRF_CACHED_FUNCTION_FOUND`具有值為零，因此`COR_PRF_JIT_CACHE`不能用做為布林的 surrogate。</span><span class="sxs-lookup"><span data-stu-id="4d2fe-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d2fe-105">語法</span><span class="sxs-lookup"><span data-stu-id="4d2fe-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="4d2fe-106">成員</span><span class="sxs-lookup"><span data-stu-id="4d2fe-106">Members</span></span>  
  
|<span data-ttu-id="4d2fe-107">成員</span><span class="sxs-lookup"><span data-stu-id="4d2fe-107">Member</span></span>|<span data-ttu-id="4d2fe-108">描述</span><span class="sxs-lookup"><span data-stu-id="4d2fe-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="4d2fe-109">搜尋找不到函式。</span><span class="sxs-lookup"><span data-stu-id="4d2fe-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="4d2fe-110">搜尋找不到函式。</span><span class="sxs-lookup"><span data-stu-id="4d2fe-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d2fe-111">需求</span><span class="sxs-lookup"><span data-stu-id="4d2fe-111">Requirements</span></span>  
 <span data-ttu-id="4d2fe-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d2fe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d2fe-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4d2fe-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4d2fe-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d2fe-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d2fe-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d2fe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d2fe-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d2fe-116">See Also</span></span>  
 [<span data-ttu-id="4d2fe-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="4d2fe-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
