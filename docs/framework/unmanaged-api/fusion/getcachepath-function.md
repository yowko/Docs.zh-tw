---
title: "GetCachePath 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 371dab83d7441681b9d6bd5723bcd8c3caadb50e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getcachepath-function"></a><span data-ttu-id="6bd7f-102">GetCachePath 函式</span><span class="sxs-lookup"><span data-stu-id="6bd7f-102">GetCachePath Function</span></span>
<span data-ttu-id="6bd7f-103">取得使用指定的旗標的快取組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="6bd7f-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bd7f-104">語法</span><span class="sxs-lookup"><span data-stu-id="6bd7f-104">Syntax</span></span>  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6bd7f-105">參數</span><span class="sxs-lookup"><span data-stu-id="6bd7f-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="6bd7f-106">[in][ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)值，指出快取的組件的來源。</span><span class="sxs-lookup"><span data-stu-id="6bd7f-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="6bd7f-107">[out]路徑傳回的指標。</span><span class="sxs-lookup"><span data-stu-id="6bd7f-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="6bd7f-108">[in、 out]所要求的最大長度的`pwzCachePath`，並在傳回時，實際長度後`pwzCachePath`。</span><span class="sxs-lookup"><span data-stu-id="6bd7f-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bd7f-109">需求</span><span class="sxs-lookup"><span data-stu-id="6bd7f-109">Requirements</span></span>  
 <span data-ttu-id="6bd7f-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd7f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bd7f-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6bd7f-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6bd7f-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bd7f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd7f-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="6bd7f-113">See Also</span></span>  
 [<span data-ttu-id="6bd7f-114">ASM_CACHE_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="6bd7f-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)  
 [<span data-ttu-id="6bd7f-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="6bd7f-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
