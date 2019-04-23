---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08937e87b8bd2249b8608f8ec1ed1f7734961b3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184830"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法
[受到 [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] 和更新版本的支援]  
  
 啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況的回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>參數  
 `enableExceptionsOutsideOfJMC`  
 [in]  
  
## <a name="remarks"></a>備註  
 如果 `enableExceptionsOutsideOfJMC` 的值為 `false`：  
  
-   DEBUG_EXCEPTION_FIRST_CHANCE 例外狀況不會導致回呼偵錯工具。  
  
-   DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外狀況不會導致回呼偵錯工具如果例外狀況絕不會逸出到使用者程式碼 （也就是從例外狀況來源到例外狀況處理常式的路徑有沒有標記為 JustMyCode 或 JMC 的方法）。  
  
 `enableExceptionsOutsideOfJMC` 的預設值為 `true`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess8 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
