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
ms.openlocfilehash: 08fe81321e958d61c1aae86ae366077b563dba3e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="f05ed-102">COR_PRF_JIT_CACHE 列舉</span><span class="sxs-lookup"><span data-stu-id="f05ed-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="f05ed-103">指出快取的函式搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="f05ed-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f05ed-104">`COR_PRF_CACHED_FUNCTION_FOUND`具有值為零，因此`COR_PRF_JIT_CACHE`不能用做為布林的 surrogate。</span><span class="sxs-lookup"><span data-stu-id="f05ed-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f05ed-105">語法</span><span class="sxs-lookup"><span data-stu-id="f05ed-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="f05ed-106">成員</span><span class="sxs-lookup"><span data-stu-id="f05ed-106">Members</span></span>  
  
|<span data-ttu-id="f05ed-107">成員</span><span class="sxs-lookup"><span data-stu-id="f05ed-107">Member</span></span>|<span data-ttu-id="f05ed-108">說明</span><span class="sxs-lookup"><span data-stu-id="f05ed-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="f05ed-109">搜尋找不到函式。</span><span class="sxs-lookup"><span data-stu-id="f05ed-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="f05ed-110">搜尋找不到函式。</span><span class="sxs-lookup"><span data-stu-id="f05ed-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f05ed-111">需求</span><span class="sxs-lookup"><span data-stu-id="f05ed-111">Requirements</span></span>  
 <span data-ttu-id="f05ed-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f05ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f05ed-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f05ed-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f05ed-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f05ed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f05ed-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f05ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f05ed-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f05ed-116">See Also</span></span>  
 [<span data-ttu-id="f05ed-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="f05ed-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
