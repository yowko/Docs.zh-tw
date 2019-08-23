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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3219554cf953b8de31e236b2f484478172673f7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915012"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue Interface

ICorDebugReferenceValue 的子類別, 代表偵錯工具已為其建立垃圾收集控制碼的參考值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Dispose 方法](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|釋放這個`ICorDebugHandleValue`物件所參考的控制碼, 而不明確釋放介面指標。|  
|[GetHandleType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|取得 CorDebugHandleType 值, 描述這個`ICorDebugHandleValue`所參考的控制碼種類。|  
  
## <a name="remarks"></a>備註  
 在`ICorDebugReferenceValue`執行已調試的程式碼時, 物件會因為中斷而失效。 會透過中斷和接續來維護其參考,直到明確釋放為止。`ICorDebugHandleValue`  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
