---
title: LoggingLevelEnum 列舉
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
ms.openlocfilehash: 01e1eafd9955a0876f77e34eb73c2a3fc6d815c2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139209"
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum 列舉
指出當 Managed 執行緒記錄事件時，寫入至事件記錄檔之描述性訊息的嚴重性層級。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`LTraceLevel0`|訊息是追蹤層級0。|  
|`LTraceLevel1`|訊息是追蹤層級1。|  
|`LTraceLevel2`|訊息是追蹤層級2。|  
|`LTraceLevel3`|訊息是追蹤層級3。|  
|`LTraceLevel4`|訊息是追蹤層級4。|  
|`LStatusLevel0`|訊息是狀態層級0。|  
|`LStatusLevel1`|訊息是狀態層級1。|  
|`LStatusLevel2`|訊息是狀態層級2。|  
|`LStatusLevel3`|訊息是狀態層級3。|  
|`LStatusLevel4`|訊息是狀態層級4。|  
|`LWarningLevel`|訊息是警告層級。|  
|`LErrorLevel`|訊息為錯誤層級。|  
|`LPanicLevel`|訊息是一個驚慌層級。|  
  
## <a name="remarks"></a>備註  
 Common language runtime （CLR）會呼叫[ICorDebugManagedCallback：： LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)方法，以通知偵錯工具 managed 執行緒已記錄事件。 CLR 會傳遞 `LoggingLevelEnum` 列舉的值，指出 managed 執行緒寫入事件記錄檔之訊息的嚴重性層級。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Diagnostics.EventLog>
- [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
