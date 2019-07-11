---
title: ICorDebugExceptionDebugEvent::GetStackPointer 方法
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b30fae0e0a6b6cca64581ecafe78621c8f0068b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754303"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a>ICorDebugExceptionDebugEvent::GetStackPointer 方法
取得這個例外狀況偵錯事件的堆疊指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a>參數  
 `pStackPointer`  
 [out] 這個例外狀況偵錯事件之堆疊指標的位址指標。 如需詳細資訊，請參閱＜備註＞一節。  
  
## <a name="remarks"></a>備註  
 這個堆疊指標的意義取決於事件類型，如下表所示。  
  
|事件類型|`pStackPointer` 值的意義|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|擲回例外狀況之框架的堆疊指標。|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|最接近擲回例外狀況位置之使用者程式碼框架的堆疊指標。|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|包含 catch 處理常式之框架的堆疊指標。|  
|[MANAGED_EXCEPTION_UNHANDLED](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|`pStackPointer` 為 **null**。|  
  
> [!NOTE]
>  這個方法僅適用於 .NET Native。  
  
 事件類型是由[icordebugdebugevent:: Geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugExceptionDebugEvent 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
