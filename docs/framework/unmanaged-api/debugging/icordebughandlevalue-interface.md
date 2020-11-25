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
ms.openlocfilehash: e695a93036e00e651ecababb0e1407661bcc48d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729079"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue Interface

ICorDebugReferenceValue 的子類別，表示偵錯工具已建立垃圾收集控制碼的參考值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Dispose 方法](icordebughandlevalue-dispose-method.md)|釋放這個物件所參考的控制碼， `ICorDebugHandleValue` 而不明確釋放介面指標。|  
|[GetHandleType 方法](icordebughandlevalue-gethandletype-method.md)|取得描述這個所參考之控制碼類型的 CorDebugHandleType 值 `ICorDebugHandleValue` 。|  
  
## <a name="remarks"></a>備註  

 `ICorDebugReferenceValue`物件在執行已偵錯工具代碼時中斷，會失效。 `ICorDebugHandleValue`會維護其在中斷和接續的參考，直到明確釋放為止。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
