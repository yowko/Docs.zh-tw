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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b0a5d80d984a3c696b178c4d8c936bd47354945
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135235"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet 介面
代表目前正在執行的程式碼的電腦上的可用暫存器組。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetRegisters 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|取得每個暫存器值 （在電腦上目前正在執行的程式碼） 所指定的位元遮罩。|  
|[GetRegistersAvailable 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|取得位元遮罩，指出其會登錄在此`ICorDebugRegisterSet`目前可用。|  
|[GetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|取得目前執行緒的內容。|  
|[SetRegisters 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|未實作適用於.NET Framework 2.0 版。|  
|[SetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|.NET Framework 2.0 中，未實作。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugRegisterSet`介面支援僅 32 位元暫存器。 使用[ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)需要其他暫存器，例如 IA-64 平台上的介面。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugRegisterSet2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
