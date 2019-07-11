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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9659dd835bb60adf8471f73ed45b6588cf15126f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752594"
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
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`LTraceLevel0`|此訊息為 「 追蹤層級 0。|  
|`LTraceLevel1`|此訊息為 「 追蹤層級 1。|  
|`LTraceLevel2`|此訊息為 「 追蹤層級 2。|  
|`LTraceLevel3`|此訊息為 「 追蹤層級 3。|  
|`LTraceLevel4`|此訊息為 「 追蹤層級 4。|  
|`LStatusLevel0`|為狀態層級 0 的訊息。|  
|`LStatusLevel1`|為狀態層級 1 的訊息。|  
|`LStatusLevel2`|此訊息為狀態層級 2。|  
|`LStatusLevel3`|為狀態層級 3 的訊息。|  
|`LStatusLevel4`|此訊息為狀態層級 4。|  
|`LWarningLevel`|訊息是警告層級。|  
|`LErrorLevel`|訊息是錯誤層級。|  
|`LPanicLevel`|此訊息為異常的層級。|  
  
## <a name="remarks"></a>備註  
 Common language runtime (CLR) 呼叫[icordebugmanagedcallback:: Logmessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)方法來通知偵錯工具 managed 的執行緒已記錄事件。 CLR 值傳遞給`LoggingLevelEnum`表示 managed 的執行緒寫入事件記錄檔訊息的嚴重性層級的列舉。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.EventLog>
- [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
