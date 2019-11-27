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
ms.openlocfilehash: 57d6ba77081536eb2bce0bf62d43ac080b2f5554
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447349"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="cd3a8-102">COR_PRF_JIT_CACHE 列舉</span><span class="sxs-lookup"><span data-stu-id="cd3a8-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="cd3a8-103">指出快取的函式搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="cd3a8-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd3a8-104">`COR_PRF_CACHED_FUNCTION_FOUND` 的值為零，所以 `COR_PRF_JIT_CACHE` 無法做為布林值代理使用。</span><span class="sxs-lookup"><span data-stu-id="cd3a8-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd3a8-105">語法</span><span class="sxs-lookup"><span data-stu-id="cd3a8-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="cd3a8-106">Members</span><span class="sxs-lookup"><span data-stu-id="cd3a8-106">Members</span></span>  
  
|<span data-ttu-id="cd3a8-107">成員</span><span class="sxs-lookup"><span data-stu-id="cd3a8-107">Member</span></span>|<span data-ttu-id="cd3a8-108">描述</span><span class="sxs-lookup"><span data-stu-id="cd3a8-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="cd3a8-109">搜尋找到函式。</span><span class="sxs-lookup"><span data-stu-id="cd3a8-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="cd3a8-110">搜尋找不到函數。</span><span class="sxs-lookup"><span data-stu-id="cd3a8-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd3a8-111">需求</span><span class="sxs-lookup"><span data-stu-id="cd3a8-111">Requirements</span></span>  
 <span data-ttu-id="cd3a8-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd3a8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd3a8-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd3a8-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd3a8-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd3a8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd3a8-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd3a8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd3a8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd3a8-116">See also</span></span>

- [<span data-ttu-id="cd3a8-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="cd3a8-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
