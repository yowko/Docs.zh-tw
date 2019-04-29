---
title: CorDebugUnmappedStop 列舉
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1cea8adcd12ecb3078e4469e6b018ed49064e0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723312"
---
# <a name="cordebugunmappedstop-enumeration"></a>CorDebugUnmappedStop 列舉
指定可在步進器執行程式碼時觸發暫止的未對應程式碼類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`STOP_NONE`|不會停止任何類型的未對應的程式碼。|  
|`STOP_PROLOG`|停止在初構程式碼中。|  
|`STOP_EPILOG`|終解程式碼中停止。|  
|`STOP_NO_MAPPING_INFO`|沒有對應資訊的程式碼中停止。|  
|`STOP_OTHER_UNMAPPED`|停止未對應的程式碼，並不適用於初構、 終解、 沒有對應資訊或未受管理的類別目錄中。|  
|`STOP_UNMANAGED`|停止在 unmanaged 程式碼。 此值就有效只能搭配 interop 偵錯。|  
|`STOP_ALL`|停止所有類型的未對應的程式碼。|  
  
## <a name="remarks"></a>備註  
 使用[icordebugstepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)方法來設定旗標，指定在其中將會停止步進未對應的程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
