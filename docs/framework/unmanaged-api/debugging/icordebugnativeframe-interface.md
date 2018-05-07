---
title: ICorDebugNativeFrame Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7996d5800e99d8e6161e24f34604aff3e4e906bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugnativeframe-interface1"></a>ICorDebugNativeFrame Interface1
ICorDebugFrame 用於原生框架的特殊的實作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CanSetIP 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|取得值，指出是否安全指令指標設在原生程式碼中指定的位移位置。|  
|[GetIP 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|取得原生程式碼中堆疊框架的位移。|  
|[GetLocalDoubleRegisterValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|取得表示的引數或兩個原生框架記憶體暫存器中儲存的本機變數的值 ICorDebugValue 指標。|  
|[GetLocalMemoryRegisterValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|取得指標`ICorDebugValue`，代表本機變數，其中的低位元會儲存在指定的暫存器和高的位元會儲存在指定的記憶體位址的值。|  
|[GetLocalMemoryValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|取得指標`ICorDebugValue`表示儲存在指定的記憶體位址變數的值。|  
|[GetLocalRegisterMemoryValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|取得指標`ICorDebugValue`，代表本機變數，其中高的位元會儲存在指定的暫存器和低位元會儲存在指定的記憶體位址的值|  
|[GetLocalRegisterValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|取得指標`ICorDebugValue`表示的引數，或是儲存在指定的原生暫存器中的本機變數的值。|  
|[GetRegisterSet 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|取得指標[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) ，代表這個設定的暫存器`ICorDebugNativeFrame`。|  
|[SetIP 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|將指定的位移位置的指令指標原生程式碼。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
