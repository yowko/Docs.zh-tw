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
ms.openlocfilehash: b1c28f32a4b24393483241bd2d7d6f550b8b65ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796902"
---
# <a name="getcachepath-function"></a><span data-ttu-id="8f25a-102">GetCachePath 函式</span><span class="sxs-lookup"><span data-stu-id="8f25a-102">GetCachePath Function</span></span>
<span data-ttu-id="8f25a-103">使用指定的旗標，取得快取元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="8f25a-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f25a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f25a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f25a-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f25a-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="8f25a-106">在[ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md)值，表示快取元件的來源。</span><span class="sxs-lookup"><span data-stu-id="8f25a-106">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="8f25a-107">脫銷傳回到路徑的指標。</span><span class="sxs-lookup"><span data-stu-id="8f25a-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="8f25a-108">[in、out]要求的最大長度`pwzCachePath`，以及傳回時的實際`pwzCachePath`長度。</span><span class="sxs-lookup"><span data-stu-id="8f25a-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f25a-109">需求</span><span class="sxs-lookup"><span data-stu-id="8f25a-109">Requirements</span></span>  
 <span data-ttu-id="8f25a-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f25a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f25a-111">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="8f25a-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8f25a-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f25a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f25a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f25a-113">See also</span></span>

- [<span data-ttu-id="8f25a-114">ASM_CACHE_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="8f25a-114">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="8f25a-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="8f25a-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
