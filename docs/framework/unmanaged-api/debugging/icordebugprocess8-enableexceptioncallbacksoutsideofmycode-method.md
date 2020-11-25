---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: 750d2a2d69c74e147c34c9c496079ee48ac04b42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732537"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法

[在 .NET Framework 4.6 和更新版本中支援]  
  
 啟用或停用特定類型的 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 例外狀況回呼。  
  
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
  
- DEBUG_EXCEPTION_FIRST_CHANCE 例外狀況不會導致回呼偵錯工具。  
  
- 如果例外狀況絕不會逸出到使用者程式碼中 (也就是從例外狀況來源到例外狀況處理常式的路徑沒有標記為 JustMyCode 或 JMC 的方法)，則 DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外狀況不會導致回呼偵錯工具。  
  
 `enableExceptionsOutsideOfJMC` 的預設值為 `true`。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess8 介面](icordebugprocess8-interface.md)
- [偵錯介面](debugging-interfaces.md)
