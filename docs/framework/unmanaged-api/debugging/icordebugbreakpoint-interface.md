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
ms.openlocfilehash: 29bb84341c2cb4177c43f798d25a1a6d50099aa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122783"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint 介面

代表函式中的中斷點，或值的監看點。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Activate 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|設定此 `ICorDebugBreakpoint`的作用中狀態。|  
|[IsActive 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|取得值，指出此 `ICorDebugBreakpoint` 是否為使用中。|  
  
## <a name="remarks"></a>備註  
 中斷點不直接支援條件運算式。 如果需要這類功能，偵錯工具必須在 `ICorDebugBreakpoint`上執行。  
  
 ICorDebugFunctionBreakpoint 介面會擴充 `ICorDebugBreakpoint`，以支援函式內的中斷點。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
