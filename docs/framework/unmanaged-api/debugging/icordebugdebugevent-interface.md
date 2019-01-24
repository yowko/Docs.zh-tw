---
title: ICorDebugDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e9a7efadea7960eadccfa1637489ed14bbeb26f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576313"
---
# <a name="icordebugdebugevent-interface"></a>ICorDebugDebugEvent 介面
定義所有 `ICorDebug` 偵錯事件衍生的來源基底介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetEventKind 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|指出這個 `ICorDebugDebugEvent` 物件所代表的事件類型。|  
|[GetThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|取得發生事件的執行緒。|  
  
## <a name="remarks"></a>備註  
 下列介面衍生自 `ICorDebugDebugEvent` 介面：  
  
-   [ICorDebugExceptionDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [ICorDebugModuleDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  這個介面僅適用於 .NET 原生。 嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
