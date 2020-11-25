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
ms.openlocfilehash: 940810288b72be0d4dfc5366176663c22c369ebb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712374"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet 介面

代表目前正在執行程式碼之電腦上可用的暫存器集。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetRegisters 方法](icordebugregisterset-getregisters-method.md)|取得電腦上每個登錄 (的值，此電腦上目前正在執行位元遮罩所指定的程式碼) 。|  
|[GetRegistersAvailable 方法](icordebugregisterset-getregistersavailable-method.md)|取得位元遮罩，指出目前有哪些暫存器 `ICorDebugRegisterSet` 可供使用。|  
|[GetThreadContext 方法](icordebugregisterset-getthreadcontext-method.md)|取得目前線程的內容。|  
|[SetRegisters 方法](icordebugregisterset-setregisters-method.md)|未針對 .NET Framework 版本2.0 執行。|  
|[SetThreadContext 方法](icordebugregisterset-setthreadcontext-method.md)|未針對 .NET Framework 2.0 執行。|  
  
## <a name="remarks"></a>備註  

 `ICorDebugRegisterSet`介面僅支援32位暫存器。 在需要其他暫存器的平臺（例如 IA-64）上使用 [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) 介面。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [ICorDebugRegisterSet2 介面](icordebugregisterset2-interface.md)
