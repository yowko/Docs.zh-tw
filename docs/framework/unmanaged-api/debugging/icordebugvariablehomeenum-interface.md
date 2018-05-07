---
title: ICorDebugVariableHomeEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a80a334d1b586aec30c6cf2715d7fb841bc76929
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablehomeenum-interface"></a>ICorDebugVariableHomeEnum 介面
提供的本機變數和引數的函式中的列舉值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Next 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|取得指定的數目[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)包含本機變數和引數的函式中的相關資訊的執行個體。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugVariableHomeEnum`介面會實作 ICorDebugEnum 介面。  
  
 `ICorDebugVariableHomeEnum`執行個體填入[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)藉由呼叫的執行個體[ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)方法。 每個[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)集合中的執行個體代表本機變數或引數的函式中。 [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)可列舉集合中的物件，藉由呼叫[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugVariableHome 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
