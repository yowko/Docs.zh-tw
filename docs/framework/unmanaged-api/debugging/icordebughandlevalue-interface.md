---
title: ICorDebugHandleValue Interface
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: 406468fc6e2b68e8c8e1dfbd0f0f18cce3f013ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794449"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue Interface

ICorDebugReferenceValue 的子類別，代表偵錯工具已為其建立垃圾收集控制碼的參考值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Dispose 方法](icordebughandlevalue-dispose-method.md)|釋放這個 `ICorDebugHandleValue` 物件所參考的控制碼，而不明確釋放介面指標。|  
|[GetHandleType 方法](icordebughandlevalue-gethandletype-method.md)|取得描述此 `ICorDebugHandleValue`所參考之控制碼種類的 CorDebugHandleType 值。|  
  
## <a name="remarks"></a>備註  
 在執行已調試的程式碼時，`ICorDebugReferenceValue` 物件會使其失效。 `ICorDebugHandleValue` 會透過中斷和接續來維護其參考，直到明確釋放為止。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
