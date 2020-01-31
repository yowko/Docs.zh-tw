---
title: ICorDebugRegisterSet 介面
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: f435db28d5c85d576f69e7612841fc46ae142332
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792076"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet 介面
代表目前執行程式碼的電腦上可用的暫存器集合。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetRegisters 方法](icordebugregisterset-getregisters-method.md)|取得位元遮罩所指定之每個暫存器（目前執行程式碼的電腦）的值。|  
|[GetRegistersAvailable 方法](icordebugregisterset-getregistersavailable-method.md)|取得位元遮罩，指出此 `ICorDebugRegisterSet` 中的哪些暫存器目前可供使用。|  
|[GetThreadContext 方法](icordebugregisterset-getthreadcontext-method.md)|取得目前線程的內容。|  
|[SetRegisters 方法](icordebugregisterset-setregisters-method.md)|未針對 .NET Framework 版本2.0 進行執行。|  
|[SetThreadContext 方法](icordebugregisterset-setthreadcontext-method.md)|未針對 .NET Framework 2.0 執行。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugRegisterSet` 介面僅支援32位暫存器。 在需要額外暫存器的平臺（例如 IA-64）上使用[ICorDebugRegisterSet2](icordebugregisterset2-interface.md)介面。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [ICorDebugRegisterSet2 介面](icordebugregisterset2-interface.md)
