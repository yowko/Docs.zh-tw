---
title: ICorDebugRegisterSet2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: c04bb3a7584fcb783af929e87713dbec67ad705f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712313"
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2 介面

針對具有超過64暫存器的硬體平臺，擴充 [ICorDebugRegisterSet](icordebugregisterset-interface.md) 介面的功能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetRegisters 方法](icordebugregisterset2-getregisters-method.md)|取得電腦上每個登錄 (的值，此電腦上目前正在執行位元遮罩所指定的程式碼) 。|  
|[GetRegistersAvailable 方法](icordebugregisterset2-getregistersavailable-method.md)|取得位元組陣列，以提供可用暫存器的點陣圖。|  
|[SetRegisters 方法](icordebugregisterset2-setregisters-method.md)|未在 .NET Framework 版本2.0 中執行。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [ICorDebugRegisterSet 介面](icordebugregisterset-interface.md)
