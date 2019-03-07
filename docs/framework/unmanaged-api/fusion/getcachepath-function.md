---
title: GetCachePath 函式
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc29c5f975424e3dbe91e206f6a05f830d760398
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472647"
---
# <a name="getcachepath-function"></a><span data-ttu-id="a8644-102">GetCachePath 函式</span><span class="sxs-lookup"><span data-stu-id="a8644-102">GetCachePath Function</span></span>
<span data-ttu-id="a8644-103">取得快取的組件，並使用指定的旗標的路徑。</span><span class="sxs-lookup"><span data-stu-id="a8644-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8644-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8644-104">Syntax</span></span>  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8644-105">參數</span><span class="sxs-lookup"><span data-stu-id="a8644-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="a8644-106">[in][ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)值，指出快取的組件的來源。</span><span class="sxs-lookup"><span data-stu-id="a8644-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="a8644-107">[out]至路徑傳回的指標。</span><span class="sxs-lookup"><span data-stu-id="a8644-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="a8644-108">[in、 out]要求最大長度`pwzCachePath`，並會在傳回時，實際長度時`pwzCachePath`。</span><span class="sxs-lookup"><span data-stu-id="a8644-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8644-109">需求</span><span class="sxs-lookup"><span data-stu-id="a8644-109">Requirements</span></span>  
 <span data-ttu-id="a8644-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8644-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8644-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a8644-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a8644-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8644-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8644-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8644-113">See also</span></span>
- [<span data-ttu-id="a8644-114">ASM_CACHE_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="a8644-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)
- [<span data-ttu-id="a8644-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="a8644-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
