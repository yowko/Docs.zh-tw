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
ms.openlocfilehash: 161358fab9a4601e7b718321273d493bd84a3228
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792017"
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2 介面
針對具有64以上暫存器的硬體平臺，擴充[ICorDebugRegisterSet](icordebugregisterset-interface.md)介面的功能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetRegisters 方法](icordebugregisterset2-getregisters-method.md)|取得位元遮罩所指定之每個暫存器（目前執行程式碼的電腦）的值。|  
|[GetRegistersAvailable 方法](icordebugregisterset2-getregistersavailable-method.md)|取得提供可用暫存器之點陣圖的位元組陣列。|  
|[SetRegisters 方法](icordebugregisterset2-setregisters-method.md)|未在 .NET Framework 版本2.0 中執行。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [ICorDebugRegisterSet 介面](icordebugregisterset-interface.md)
