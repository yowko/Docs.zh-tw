---
title: "ASM_CMP_FLAGS 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASM_CMP_FLAGS
api_location: fusion.dll
api_type: COM
f1_keywords: ASM_CMP_FLAGS
helpviewer_keywords: ASM_CMP_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 4d1e6700-d4be-4fbd-8796-bfb4c07abbc8
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4930a4998ace3a1cd9e60300818fcfc75702b63b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="asmcmpflags-enumeration"></a><span data-ttu-id="420c1-102">ASM_CMP_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="420c1-102">ASM_CMP_FLAGS Enumeration</span></span>
<span data-ttu-id="420c1-103">表示版本、 組建、 文化特性、 簽章，依此類推，所要比較的兩個組件的[iassemblyname:: Isequal](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="420c1-103">Indicates the version, build, culture, signature, and so on, of two assemblies to be compared by the [IAssemblyName::IsEqual](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="420c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="420c1-104">Syntax</span></span>  
  
```  
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
  
## <a name="requirements"></a><span data-ttu-id="420c1-105">需求</span><span class="sxs-lookup"><span data-stu-id="420c1-105">Requirements</span></span>  
 <span data-ttu-id="420c1-106">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="420c1-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="420c1-107">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="420c1-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="420c1-108">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="420c1-108">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="420c1-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="420c1-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="420c1-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="420c1-110">See Also</span></span>  
 [<span data-ttu-id="420c1-111">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="420c1-111">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="420c1-112">融合列舉</span><span class="sxs-lookup"><span data-stu-id="420c1-112">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
