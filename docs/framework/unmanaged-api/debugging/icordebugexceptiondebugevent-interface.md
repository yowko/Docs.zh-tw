---
title: ICorDebugExceptionDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: 168ba2945608a5b26432c5a0f583e5d406f6ce9b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782822"
---
# <a name="icordebugexceptiondebugevent-interface"></a>ICorDebugExceptionDebugEvent 介面
擴充[ICorDebugDebugEvent](icordebugdebugevent-interface.md)介面，以支援例外狀況事件。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetFlags 方法](icordebugexceptiondebugevent-getflags-method.md)|取得指出例外狀況是否可以被攔截的旗標。|  
|[GetNativeIP 方法](icordebugexceptiondebugevent-getnativeip-method.md)|取得這個例外狀況偵錯事件的原生介面指標。|  
|[GetStackPointer 方法](icordebugexceptiondebugevent-getstackpointer-method.md)|取得這個例外狀況偵錯事件的堆疊指標。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugExceptionDebugEvent` 介面由下列事件類型實作：  
  
- [MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)  
  
- [MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)  
  
- [MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)  
  
- [MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> 這個介面僅適用於 .NET Native。 嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
