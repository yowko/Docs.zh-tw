---
title: ASM_NAME 列舉
ms.date: 03/30/2017
api_name:
- ASM_NAME
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_NAME
helpviewer_keywords:
- ASM_NAME enumeration [.NET Framework fusion]
ms.assetid: c8b65b19-d777-428f-bc0c-0d84c78a37bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b37e9c2874448b5fff82f6a37f6ca850875f2b04
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112511"
---
# <a name="asmname-enumeration"></a><span data-ttu-id="3a7b3-102">ASM_NAME 列舉</span><span class="sxs-lookup"><span data-stu-id="3a7b3-102">ASM_NAME Enumeration</span></span>
<span data-ttu-id="3a7b3-103">表示版本、 組建、 文化特性、 簽章，依此類推，會擷取或設定其屬性之組件的[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)方法。</span><span class="sxs-lookup"><span data-stu-id="3a7b3-103">Indicates the version, build, culture, signature, and so on, of the assembly whose properties will be retrieved or set by [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a7b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a7b3-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    ASM_NAME_PUBLIC_KEY = 0,  
    ASM_NAME_PUBLIC_KEY_TOKEN,  
    ASM_NAME_HASH_VALUE,  
    ASM_NAME_NAME,  
    ASM_NAME_MAJOR_VERSION,  
    ASM_NAME_MINOR_VERSION,  
    ASM_NAME_BUILD_NUMBER,  
    ASM_NAME_REVISION_NUMBER,  
    ASM_NAME_CULTURE,  
    ASM_NAME_PROCESSOR_ID_ARRAY,  
    ASM_NAME_OSINFO_ARRAY,  
    ASM_NAME_HASH_ALGID,  
    ASM_NAME_ALIAS,  
    ASM_NAME_CODEBASE_URL,  
    ASM_NAME_CODEBASE_LASTMOD,  
    ASM_NAME_NULL_PUBLIC_KEY,  
    ASM_NAME_NULL_PUBLIC_KEY_TOKEN,  
    ASM_NAME_CUSTOM,  
    ASM_NAME_NULL_CUSTOM,   
    ASM_NAME_MVID,  
    ASM_NAME_FILE_MAJOR_VERSION,  
    ASM_NAME_FILE_MINOR_VERSION,  
    ASM_NAME_FILE_BUILD_NUMBER,  
    ASM_NAME_FILE_REVISION_NUMBER,  
    ASM_NAME_RETARGET,  
    ASM_NAME_SIGNATURE_BLOB,  
    ASM_NAME_CONFIG_MASK,  
    ASM_NAME_ARCHITECTURE,  
    ASM_NAME_MAX_PARAMS  
  
} ASM_NAME;  
```  
  
## <a name="requirements"></a><span data-ttu-id="3a7b3-105">需求</span><span class="sxs-lookup"><span data-stu-id="3a7b3-105">Requirements</span></span>  
 <span data-ttu-id="3a7b3-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a7b3-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a7b3-107">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="3a7b3-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3a7b3-108">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3a7b3-108">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="3a7b3-109">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="3a7b3-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3a7b3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a7b3-110">See also</span></span>

- [<span data-ttu-id="3a7b3-111">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="3a7b3-111">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="3a7b3-112">融合列舉</span><span class="sxs-lookup"><span data-stu-id="3a7b3-112">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
