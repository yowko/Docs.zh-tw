---
title: ICorDebugNativeFrame 介面
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: 41ac0b29ade2f78b893df72e8a17624373f6dd78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792796"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame 介面

用於原生框架的 ICorDebugFrame 特製化。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CanSetIP 方法](icordebugnativeframe-cansetip-method.md)|取得值，指出是否可以安全地將指令指標設定為機器碼中的指定位移位置。|  
|[GetIP 方法](icordebugnativeframe-getip-method.md)|取得原生程式碼的堆疊框架位移。|  
|[GetLocalDoubleRegisterValue 方法](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|取得 ICorDebugValue 的指標，代表儲存在原生框架之兩個記憶體暫存器中的引數或區域變數的值。|  
|[GetLocalMemoryRegisterValue 方法](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|取得 `ICorDebugValue` 的指標，表示本機變數的值，其中的低位會儲存在指定的暫存器中，而高位則儲存在指定的記憶體位址。|  
|[GetLocalMemoryValue 方法](icordebugnativeframe-getlocalmemoryvalue-method.md)|取得 `ICorDebugValue` 的指標，表示儲存在指定記憶體位址的本機變數值。|  
|[GetLocalRegisterMemoryValue 方法](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|取得 `ICorDebugValue` 的指標，表示本機變數的值，其中的高位會儲存在指定的暫存器中，而低位則儲存在指定的記憶體位址|  
|[GetLocalRegisterValue 方法](icordebugnativeframe-getlocalregistervalue-method.md)|取得 `ICorDebugValue` 的指標，表示引數或儲存在指定的原生暫存器中的區域變數值。|  
|[GetRegisterSet 方法](icordebugnativeframe-getregisterset-method.md)|取得[ICorDebugRegisterSet](icordebugregisterset-interface.md)的指標，表示此 `ICorDebugNativeFrame`的暫存器集。|  
|[SetIP 方法](icordebugnativeframe-setip-method.md)|將指令指標設定為原生程式碼中指定的位移位置。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
