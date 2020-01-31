---
title: ICorDebugModuleDebugEvent 介面
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: a2c7eaa8a2c811c1696024d9af4b715cc49e7caa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792889"
---
# <a name="icordebugmoduledebugevent-interface"></a>ICorDebugModuleDebugEvent 介面
擴充[ICorDebugDebugEvent](icordebugdebugevent-interface.md)介面，以支援模組層級事件。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetModule 方法](icordebugmoduledebugevent-getmodule-method.md)|取得剛載入或卸載的合併模組。|  
  
## <a name="remarks"></a>備註  
 [MODULE_LOADED](cordebugdebugeventkind-enumeration.md)和[MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md)事件種類會執行此介面。  
  
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
