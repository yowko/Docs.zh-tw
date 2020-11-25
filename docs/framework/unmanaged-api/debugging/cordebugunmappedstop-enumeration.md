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
ms.openlocfilehash: e251bf67adcaf2bbd6565eda068d487eb0d70efd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725765"
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
  
|member|描述|  
|------------|-----------------|  
|`STOP_NONE`|請勿在任何未對應的程式碼類型中停止。|  
|`STOP_PROLOG`|在初構程式碼中停止。|  
|`STOP_EPILOG`|在終解程式碼中停止。|  
|`STOP_NO_MAPPING_INFO`|在沒有對應資訊的程式碼中停止。|  
|`STOP_OTHER_UNMAPPED`|在未對應的程式碼中停止，但不符合初構、終解、無對應資訊或非受控類別。|  
|`STOP_UNMANAGED`|停止非受控碼。 此值僅適用于 interop 的偵錯工具。|  
|`STOP_ALL`|在所有未對應的程式碼類型中停止。|  
  
## <a name="remarks"></a>備註  

 您可以使用 [ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) 方法來設定旗標，以指定將停止執行程式的未對應程式碼。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
