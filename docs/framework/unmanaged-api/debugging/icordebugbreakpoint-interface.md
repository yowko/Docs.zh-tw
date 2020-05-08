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
ms.openlocfilehash: b92c3d3328c657762ed002155ef4947a9292b19e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894735"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint 介面

代表函式中的中斷點，或值的監看點。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Activate 方法](icordebugbreakpoint-activate-method.md)|設定這個`ICorDebugBreakpoint`的作用中狀態。|  
|[IsActive 方法](icordebugbreakpoint-isactive-method.md)|取得值，指出這個`ICorDebugBreakpoint`是否為使用中。|  
  
## <a name="remarks"></a>備註  
 中斷點不直接支援條件運算式。 如果需要這類功能，偵錯工具必須在之上執行`ICorDebugBreakpoint`。  
  
 ICorDebugFunctionBreakpoint 介面會擴充`ICorDebugBreakpoint`以支援函式內的中斷點。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
