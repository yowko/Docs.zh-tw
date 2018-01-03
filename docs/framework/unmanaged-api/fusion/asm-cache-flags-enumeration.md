---
title: "ASM_CACHE_FLAGS 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASM_CACHE_FLAGS
api_location: fusion.dll
api_type: COM
f1_keywords: ASM_CACHE_FLAGS
helpviewer_keywords: ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87dce9a2daf7067409d78a9f389695b6b01f23c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="asmcacheflags-enumeration"></a>ASM_CACHE_FLAGS 列舉
表示所表示之組件的來源[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)在全域組件快取中。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|使用 Ngen.exe 列舉快取的先行編譯的組件。|  
|`ASM_CACHE_GAC`|列舉全域組件快取。|  
|`ASM_CACHE_DOWNLOAD`|列舉視已下載，或者已陰影複製的組件。|  
|`ASM_CACHE_ROOT`|表示[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)函式應傳回至全域組件快取的 common language runtime (CLR) 2.0 版的路徑。 呼叫內容中，才有意義[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)。|  
|`ASM_CACHE_ROOT_EX`|表示[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)函式應傳回至全域組件快取路徑 clr 第 4 版。 呼叫內容中，才有意義[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [GetCachePath 函式](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 [IAssemblyCacheItem 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 [融合列舉](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
