---
title: "ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f13236c865f9a57d77ebf83ab48e010f06ef08e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法
[受到 [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] 和更新版本的支援]  
  
 啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
#### <a name="parameters"></a>參數  
 `enableExceptionsOutsideOfJMC`  
 [in]  
  
## <a name="remarks"></a>備註  
 如果 `enableExceptionsOutsideOfJMC` 的值為 `false`：  
  
-   DEBUG_EXCEPTION_FIRST_CHANCE 例外狀況不會導致回呼偵錯工具。  
  
-   DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外狀況不會導致回呼偵錯工具如果例外狀況絕不會逸出到使用者程式碼 （也就是從例外狀況來源到例外狀況處理常式的路徑具有標記為 JustMyCode 或 jmc 的方法沒有任何方法）。  
  
 `enableExceptionsOutsideOfJMC` 的預設值為 `true`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorDebugProcess8 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
