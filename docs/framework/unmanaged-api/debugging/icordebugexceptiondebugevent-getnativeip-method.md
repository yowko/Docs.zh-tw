---
title: ICorDebugExceptionDebugEvent::GetNativeIP 方法
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaa1a160bb316831540f68713647dbdc4b0f6895
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951843"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a>ICorDebugExceptionDebugEvent::GetNativeIP 方法
取得這個例外狀況偵錯事件的原生指令指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a>參數  
 `pIP`  
 [out] 這個例外狀況偵錯事件之指令指標的指標。 如需詳細資訊，請參閱＜備註＞一節。  
  
## <a name="remarks"></a>備註  
 這個指令指標的意義取決於事件類型，如下表所示。  
  
|事件類型|`pStackPointer` 值的意義|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|失敗指令的位址。|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|[GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)方法所表示的框架中的程式碼位址，如果未引發任何例外狀況，則執行會繼續。 例外狀況不一定會在這個框架中執行不同的程式碼 (例如 `try/catch/finally` 子句的 catch 區塊)。|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|在 [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) 方法所指示的框架中，`catch`處理常式執行將在其中啟動的程式碼位址。|  
|[MANAGED_EXCEPTION_UNHANDLED](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|`pIP` 為 0。|  
  
 事件種類可從[ICorDebugDebugEvent：： GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法取得。  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugExceptionDebugEvent 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
