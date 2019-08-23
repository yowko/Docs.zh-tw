---
title: ICorDebugBreakpoint 介面
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 608c2cea79c20a43d65fcbf37ba13242fa465100
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969316"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint 介面

代表函式中的中斷點, 或值的監看點。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Activate 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|設定這個`ICorDebugBreakpoint`的作用中狀態。|  
|[IsActive 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|取得值, 指出這個`ICorDebugBreakpoint`是否為使用中。|  
  
## <a name="remarks"></a>備註  
 中斷點不直接支援條件運算式。 如果需要這類功能, 偵錯工具必須在之上`ICorDebugBreakpoint`執行。  
  
 ICorDebugFunctionBreakpoint 介面會擴充`ICorDebugBreakpoint`以支援函式內的中斷點。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
