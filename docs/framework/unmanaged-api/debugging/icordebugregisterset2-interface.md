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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f4947a9b6c0e3fd87ee474111f143d273c1d7b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2 介面
擴充的功能[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)具有 64 個以上的暫存器的硬體平台的介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetRegisters 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|取得每個暫存器值 （在電腦上目前正在執行的程式碼） 的位元遮罩所指定。|  
|[GetRegistersAvailable 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|取得位元組陣列提供的可用暫存器的點陣圖。|  
|[SetRegisters 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|未實作.NET Framework 2.0 版中。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugRegisterSet 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
