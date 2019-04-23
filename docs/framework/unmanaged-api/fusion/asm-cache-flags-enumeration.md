---
title: ASM_CACHE_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 619643eb50abc75fd10d59b38767013b2617c8cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077761"
---
# <a name="asmcacheflags-enumeration"></a><span data-ttu-id="a9b77-102">ASM_CACHE_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="a9b77-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="a9b77-103">指出所表示的組件的來源[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="a9b77-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9b77-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9b77-104">Syntax</span></span>  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="a9b77-105">成員</span><span class="sxs-lookup"><span data-stu-id="a9b77-105">Members</span></span>  
  
|<span data-ttu-id="a9b77-106">成員</span><span class="sxs-lookup"><span data-stu-id="a9b77-106">Member</span></span>|<span data-ttu-id="a9b77-107">描述</span><span class="sxs-lookup"><span data-stu-id="a9b77-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="a9b77-108">使用 Ngen.exe 列舉先行編譯的組件快取。</span><span class="sxs-lookup"><span data-stu-id="a9b77-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="a9b77-109">列舉全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="a9b77-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="a9b77-110">列舉，具有視需求下載，或者已陰影複製組件。</span><span class="sxs-lookup"><span data-stu-id="a9b77-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="a9b77-111">指出[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)函式應傳回至全域組件快取的 common language runtime (CLR) 2.0 版的路徑。</span><span class="sxs-lookup"><span data-stu-id="a9b77-111">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="a9b77-112">呼叫內容中，才有意義[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)。</span><span class="sxs-lookup"><span data-stu-id="a9b77-112">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="a9b77-113">指出[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)函式應傳回至全域組件快取路徑 clr 第 4 版。</span><span class="sxs-lookup"><span data-stu-id="a9b77-113">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="a9b77-114">呼叫內容中，才有意義[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)。</span><span class="sxs-lookup"><span data-stu-id="a9b77-114">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9b77-115">需求</span><span class="sxs-lookup"><span data-stu-id="a9b77-115">Requirements</span></span>  
 <span data-ttu-id="a9b77-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9b77-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9b77-117">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a9b77-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a9b77-118">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a9b77-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9b77-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9b77-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9b77-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9b77-120">See also</span></span>

- [<span data-ttu-id="a9b77-121">GetCachePath 函式</span><span class="sxs-lookup"><span data-stu-id="a9b77-121">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)
- [<span data-ttu-id="a9b77-122">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="a9b77-122">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
- [<span data-ttu-id="a9b77-123">融合列舉</span><span class="sxs-lookup"><span data-stu-id="a9b77-123">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
