---
title: ASM_CMP_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- ASM_CMP_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CMP_FLAGS
helpviewer_keywords:
- ASM_CMP_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 4d1e6700-d4be-4fbd-8796-bfb4c07abbc8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a56785d84a07122080efda22d41ec43721474789
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795272"
---
# <a name="asm_cmp_flags-enumeration"></a><span data-ttu-id="90aed-102">ASM_CMP_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="90aed-102">ASM_CMP_FLAGS Enumeration</span></span>
<span data-ttu-id="90aed-103">指出要由[IAssemblyName：： IsEqual](iassemblyname-isequal-method.md)方法比較的兩個元件版本、組建、文化特性、簽章等。</span><span class="sxs-lookup"><span data-stu-id="90aed-103">Indicates the version, build, culture, signature, and so on, of two assemblies to be compared by the [IAssemblyName::IsEqual](iassemblyname-isequal-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90aed-104">語法</span><span class="sxs-lookup"><span data-stu-id="90aed-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_CMPF_NAME                   = 0x1,  
    ASM_CMPF_MAJOR_VERSION          = 0x2,  
    ASM_CMPF_MINOR_VERSION          = 0x4,  
    ASM_CMPF_BUILD_NUMBER           = 0x8,  
    ASM_CMPF_REVISION_NUMBER        = 0x10,  
  
    ASM_CMPF_VERSION                =   
                 ASM_CMPF_MAJOR_VERSION |   
                 ASM_CMPF_MINOR_VERSION |   
                 ASM_CMPF_BUILD_NUMBER  |   
                 ASM_CMPF_REVISION_NUMBER,  
  
    ASM_CMPF_PUBLIC_KEY_TOKEN       = 0x20,  
    ASM_CMPF_CULTURE                = 0x40,  
    ASM_CMPF_CUSTOM                 = 0x80,  
    ASM_CMPF_DEFAULT                = 0x100,  
    ASM_CMPF_RETARGET               = 0x200,  
    ASM_CMPF_ARCHITECTURE           = 0x400,  
    ASM_CMPF_CONFIG_MASK            = 0x800,  
    ASM_CMPF_MVID                   = 0x1000,  
    ASM_CMPF_SIGNATURE              = 0x2000,  
  
    ASM_CMPF_IL_ALL                 =   
                 ASM_CMPF_NAME             |   
                 ASM_CMPF_VERSION          |   
                 ASM_CMPF_PUBLIC_KEY_TOKEN |   
                 ASM_CMPF_CULTURE,  
  
    ASM_CMPF_IL_NO_VERSION          =   
                 ASM_CMPF_NAME             |   
                 ASM_CMPF_PUBLIC_KEY_TOKEN |   
                 ASM_CMPF_CULTURE  
  
} ASM_CMP_FLAGS;  
```  
  
## <a name="requirements"></a><span data-ttu-id="90aed-105">需求</span><span class="sxs-lookup"><span data-stu-id="90aed-105">Requirements</span></span>  
 <span data-ttu-id="90aed-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90aed-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90aed-107">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="90aed-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="90aed-108">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="90aed-108">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="90aed-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90aed-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90aed-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90aed-110">See also</span></span>

- [<span data-ttu-id="90aed-111">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="90aed-111">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="90aed-112">融合列舉</span><span class="sxs-lookup"><span data-stu-id="90aed-112">Fusion Enumerations</span></span>](fusion-enumerations.md)
