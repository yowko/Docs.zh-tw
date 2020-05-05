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
ms.openlocfilehash: 772f1f0dee260ad3752b2f89e5fbe0d6bc27b87b
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795647"
---
# <a name="cordebugunmappedstop-enumeration"></a>CorDebugUnmappedStop 列舉
指定可在步進器執行程式碼時觸發暫止的未對應程式碼類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
|member|說明|  
|------------|-----------------|  
|`STOP_NONE`|請勿在任何類型的未對應程式碼中停止。|  
|`STOP_PROLOG`|在初構程式碼中停止。|  
|`STOP_EPILOG`|停止結束程式碼。|  
|`STOP_NO_MAPPING_INFO`|在沒有對應資訊的程式碼中停止。|  
|`STOP_OTHER_UNMAPPED`|在未對應的程式碼中停止，而不符合初構、終解、無對應資訊或非受控類別。|  
|`STOP_UNMANAGED`|在未受管理的程式碼中停止。 此值僅適用于 interop 調試。|  
|`STOP_ALL`|停止所有類型的未對應程式碼。|  
  
## <a name="remarks"></a>備註  
 使用[ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md)方法來設定旗標，以指定分檔器將停止的未對應程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯列舉](debugging-enumerations.md)
