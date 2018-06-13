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
ms.openlocfilehash: ddf0f01db73a873d2dd823e1f754b970ae8aa056
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430469"
---
# <a name="asmcacheflags-enumeration"></a><span data-ttu-id="7df32-102">ASM_CACHE_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="7df32-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="7df32-103">表示所表示之組件的來源[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="7df32-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df32-104">語法</span><span class="sxs-lookup"><span data-stu-id="7df32-104">Syntax</span></span>  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="7df32-105">成員</span><span class="sxs-lookup"><span data-stu-id="7df32-105">Members</span></span>  
  
|<span data-ttu-id="7df32-106">成員</span><span class="sxs-lookup"><span data-stu-id="7df32-106">Member</span></span>|<span data-ttu-id="7df32-107">描述</span><span class="sxs-lookup"><span data-stu-id="7df32-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="7df32-108">使用 Ngen.exe 列舉快取的先行編譯的組件。</span><span class="sxs-lookup"><span data-stu-id="7df32-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="7df32-109">列舉全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="7df32-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="7df32-110">列舉視已下載，或者已陰影複製的組件。</span><span class="sxs-lookup"><span data-stu-id="7df32-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="7df32-111">表示[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)函式應傳回至全域組件快取的 common language runtime (CLR) 2.0 版的路徑。</span><span class="sxs-lookup"><span data-stu-id="7df32-111">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="7df32-112">呼叫內容中，才有意義[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)。</span><span class="sxs-lookup"><span data-stu-id="7df32-112">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="7df32-113">表示[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)函式應傳回至全域組件快取路徑 clr 第 4 版。</span><span class="sxs-lookup"><span data-stu-id="7df32-113">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="7df32-114">呼叫內容中，才有意義[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)。</span><span class="sxs-lookup"><span data-stu-id="7df32-114">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7df32-115">需求</span><span class="sxs-lookup"><span data-stu-id="7df32-115">Requirements</span></span>  
 <span data-ttu-id="7df32-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7df32-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7df32-117">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7df32-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7df32-118">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7df32-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7df32-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7df32-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df32-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7df32-120">See Also</span></span>  
 [<span data-ttu-id="7df32-121">GetCachePath 函式</span><span class="sxs-lookup"><span data-stu-id="7df32-121">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 [<span data-ttu-id="7df32-122">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="7df32-122">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 [<span data-ttu-id="7df32-123">融合列舉</span><span class="sxs-lookup"><span data-stu-id="7df32-123">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
