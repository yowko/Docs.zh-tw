---
title: "ASM_NAME 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASM_NAME
api_location: fusion.dll
api_type: COM
f1_keywords: ASM_NAME
helpviewer_keywords: ASM_NAME enumeration [.NET Framework fusion]
ms.assetid: c8b65b19-d777-428f-bc0c-0d84c78a37bc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 153daddc0a5529d2c1cddc4669c3dbb098ce7bc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="asmname-enumeration"></a><span data-ttu-id="19ae6-102">ASM_NAME 列舉</span><span class="sxs-lookup"><span data-stu-id="19ae6-102">ASM_NAME Enumeration</span></span>
<span data-ttu-id="19ae6-103">表示版本、 組建、 文化特性、 簽章，以及等等，將會擷取或設定其屬性的組件[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)方法。</span><span class="sxs-lookup"><span data-stu-id="19ae6-103">Indicates the version, build, culture, signature, and so on, of the assembly whose properties will be retrieved or set by [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19ae6-104">語法</span><span class="sxs-lookup"><span data-stu-id="19ae6-104">Syntax</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="19ae6-105">需求</span><span class="sxs-lookup"><span data-stu-id="19ae6-105">Requirements</span></span>  
 <span data-ttu-id="19ae6-106">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19ae6-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19ae6-107">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="19ae6-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="19ae6-108">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="19ae6-108">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="19ae6-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19ae6-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19ae6-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="19ae6-110">See Also</span></span>  
 [<span data-ttu-id="19ae6-111">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="19ae6-111">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="19ae6-112">融合列舉</span><span class="sxs-lookup"><span data-stu-id="19ae6-112">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
