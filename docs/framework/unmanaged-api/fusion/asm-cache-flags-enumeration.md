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
ms.openlocfilehash: 0e3e9da3db71d3e24b2a60ff032a631680055b88
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795282"
---
# <a name="asm_cache_flags-enumeration"></a>ASM_CACHE_FLAGS 列舉
指出全域組件快取中[IAssemblyCacheItem](iassemblycacheitem-interface.md)所代表之元件的來源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|使用 Ngen.exe 列舉先行編譯元件的快取。|  
|`ASM_CACHE_GAC`|列舉全域組件快取。|  
|`ASM_CACHE_DOWNLOAD`|列舉已視需要下載或已陰影複製的元件。|  
|`ASM_CACHE_ROOT`|表示[GetCachePath](getcachepath-function.md)函數應該傳回 common language RUNTIME （CLR）2.0 版的全域組件快取的路徑。 只有在呼叫[GetCachePath](getcachepath-function.md)的內容中才有意義。|  
|`ASM_CACHE_ROOT_EX`|表示[GetCachePath](getcachepath-function.md)函數應該傳回 CLR 第4版的全域組件快取的路徑。 只有在呼叫[GetCachePath](getcachepath-function.md)的內容中才有意義。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetCachePath 函式](getcachepath-function.md)
- [IAssemblyCacheItem 介面](iassemblycacheitem-interface.md)
- [融合列舉](fusion-enumerations.md)
