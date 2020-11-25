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
ms.openlocfilehash: 043dc0fdd5218d7bc6b80428d1eb891b3f01ee8c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695513"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame 介面

用於原生框架的 ICorDebugFrame 專用實作為。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CanSetIP 方法](icordebugnativeframe-cansetip-method.md)|取得值，這個值會指出是否可以安全地將指令指標設定為原生程式碼中的指定位移位置。|  
|[GetIP 方法](icordebugnativeframe-getip-method.md)|取得原生程式碼的堆疊框架位移。|  
|[GetLocalDoubleRegisterValue 方法](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|取得 ICorDebugValue 的指標，該指標表示儲存在原生框架之兩個記憶體暫存器中的引數或區域變數值。|  
|[GetLocalMemoryRegisterValue 方法](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|取得 `ICorDebugValue` 代表區域變數值的指標，該變數的低位會儲存在指定的暫存器中，而且會在指定的記憶體位址儲存高位。|  
|[GetLocalMemoryValue 方法](icordebugnativeframe-getlocalmemoryvalue-method.md)|取得的指標 `ICorDebugValue` ，該指標表示儲存在指定之記憶體位址的本機變數值。|  
|[GetLocalRegisterMemoryValue 方法](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|取得 `ICorDebugValue` 代表區域變數值的指標，該變數的最高位儲存在指定的暫存器中，而低位儲存在指定的記憶體位址|  
|[GetLocalRegisterValue 方法](icordebugnativeframe-getlocalregistervalue-method.md)|取得的指標 `ICorDebugValue` ，代表所指定原生暫存器中所儲存之引數或區域變數的值。|  
|[GetRegisterSet 方法](icordebugnativeframe-getregisterset-method.md)|取得 [ICorDebugRegisterSet](icordebugregisterset-interface.md) 的指標，該指標表示這個的註冊集 `ICorDebugNativeFrame` 。|  
|[SetIP 方法](icordebugnativeframe-setip-method.md)|將指令指標設定為原生程式碼中指定的位移位置。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
