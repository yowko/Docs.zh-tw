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
ms.openlocfilehash: d19d7ed2262db6d3c6e7f15db0e96da52f86db4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500854"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="a0e44-102">COR_PRF_JIT_CACHE 列舉</span><span class="sxs-lookup"><span data-stu-id="a0e44-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="a0e44-103">指出快取的函式搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="a0e44-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0e44-104">`COR_PRF_CACHED_FUNCTION_FOUND`的值為零，因此 `COR_PRF_JIT_CACHE` 不能用來做為布林值代理。</span><span class="sxs-lookup"><span data-stu-id="a0e44-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e44-105">語法</span><span class="sxs-lookup"><span data-stu-id="a0e44-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="a0e44-106">成員</span><span class="sxs-lookup"><span data-stu-id="a0e44-106">Members</span></span>  
  
|<span data-ttu-id="a0e44-107">成員</span><span class="sxs-lookup"><span data-stu-id="a0e44-107">Member</span></span>|<span data-ttu-id="a0e44-108">說明</span><span class="sxs-lookup"><span data-stu-id="a0e44-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="a0e44-109">搜尋找到函式。</span><span class="sxs-lookup"><span data-stu-id="a0e44-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="a0e44-110">搜尋找不到函數。</span><span class="sxs-lookup"><span data-stu-id="a0e44-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0e44-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="a0e44-111">Requirements</span></span>  
 <span data-ttu-id="a0e44-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e44-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0e44-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0e44-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0e44-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0e44-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0e44-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0e44-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e44-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0e44-116">See also</span></span>

- [<span data-ttu-id="a0e44-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="a0e44-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
