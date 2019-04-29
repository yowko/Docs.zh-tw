---
title: COR_PRF_JIT_CACHE 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_JIT_CACHE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_JIT_CACHE
helpviewer_keywords:
- COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cdbe36403f830926d611ffdc655d82ea25ddeef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599087"
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="b4728-102">COR_PRF_JIT_CACHE 列舉</span><span class="sxs-lookup"><span data-stu-id="b4728-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="b4728-103">指出快取的函式搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="b4728-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4728-104">`COR_PRF_CACHED_FUNCTION_FOUND` 值為零，因此`COR_PRF_JIT_CACHE`不能用做為布林的 surrogate。</span><span class="sxs-lookup"><span data-stu-id="b4728-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4728-105">語法</span><span class="sxs-lookup"><span data-stu-id="b4728-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="b4728-106">成員</span><span class="sxs-lookup"><span data-stu-id="b4728-106">Members</span></span>  
  
|<span data-ttu-id="b4728-107">成員</span><span class="sxs-lookup"><span data-stu-id="b4728-107">Member</span></span>|<span data-ttu-id="b4728-108">描述</span><span class="sxs-lookup"><span data-stu-id="b4728-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="b4728-109">搜尋找不到函式。</span><span class="sxs-lookup"><span data-stu-id="b4728-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="b4728-110">搜尋找不到函式。</span><span class="sxs-lookup"><span data-stu-id="b4728-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4728-111">需求</span><span class="sxs-lookup"><span data-stu-id="b4728-111">Requirements</span></span>  
 <span data-ttu-id="b4728-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4728-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4728-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4728-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4728-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4728-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4728-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4728-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4728-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4728-116">See also</span></span>

- [<span data-ttu-id="b4728-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="b4728-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
