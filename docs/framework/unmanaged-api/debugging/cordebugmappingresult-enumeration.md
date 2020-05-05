---
title: CorDebugMappingResult 列舉
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
ms.openlocfilehash: a7a450e85f7eaa765766ffa985d7c01538e2669c
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795790"
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult 列舉
提供如何取得指令指標 (IP) 值的詳細資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a>成員  
  
|member|說明|  
|------------|-----------------|  
|`MAPPING_PROLOG`|機器碼位於初構中，因此 IP 的值為0。|  
|`MAPPING_EPILOG`|機器碼為終解，因此 IP 的值是方法最後一個指令的位址。|  
|`MAPPING_NO_INFO`|方法沒有對應資訊可供使用，因此 IP 的值為0。|  
|`MAPPING_UNMAPPED_ADDRESS`|雖然有方法的對應資訊，但目前的位址無法對應至 Microsoft 中繼語言（MSIL）程式碼。 IP 的值為0。|  
|`MAPPING_EXACT`|方法可能會完全對應至 MSIL 程式碼，或已解讀框架，因此 IP 的值是正確的。|  
|`MAPPING_APPROXIMATE`|已成功對應方法，但 IP 的值可能是近似值。|  
  
## <a name="remarks"></a>備註  
 您可以使用[ICorDebugILFrame：： GetIP](icordebugilframe-getip-method.md)方法來取得指令指標的值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯列舉](debugging-enumerations.md)
