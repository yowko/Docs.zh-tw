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
ms.openlocfilehash: b8c972bcace3ba3d855a3b5eebc16e6b76994eb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450700"
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="b1c9b-102">COR_PRF_JIT_CACHE 列舉</span><span class="sxs-lookup"><span data-stu-id="b1c9b-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="b1c9b-103">指出快取的函式搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="b1c9b-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1c9b-104">`COR_PRF_CACHED_FUNCTION_FOUND` 具有值為零，因此`COR_PRF_JIT_CACHE`不能用做為布林的 surrogate。</span><span class="sxs-lookup"><span data-stu-id="b1c9b-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1c9b-105">語法</span><span class="sxs-lookup"><span data-stu-id="b1c9b-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="b1c9b-106">成員</span><span class="sxs-lookup"><span data-stu-id="b1c9b-106">Members</span></span>  
  
|<span data-ttu-id="b1c9b-107">成員</span><span class="sxs-lookup"><span data-stu-id="b1c9b-107">Member</span></span>|<span data-ttu-id="b1c9b-108">描述</span><span class="sxs-lookup"><span data-stu-id="b1c9b-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="b1c9b-109">搜尋找不到函式。</span><span class="sxs-lookup"><span data-stu-id="b1c9b-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="b1c9b-110">搜尋找不到函式。</span><span class="sxs-lookup"><span data-stu-id="b1c9b-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1c9b-111">需求</span><span class="sxs-lookup"><span data-stu-id="b1c9b-111">Requirements</span></span>  
 <span data-ttu-id="b1c9b-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1c9b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1c9b-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b1c9b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b1c9b-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1c9b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1c9b-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1c9b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c9b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1c9b-116">See Also</span></span>  
 [<span data-ttu-id="b1c9b-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="b1c9b-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
