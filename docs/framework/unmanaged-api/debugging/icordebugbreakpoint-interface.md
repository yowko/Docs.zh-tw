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
ms.openlocfilehash: 0c84a91c7da553d0c84a4995b4744576d861dcb9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730197"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint 介面

表示函式中的中斷點，或值的監看點。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Activate 方法](icordebugbreakpoint-activate-method.md)|設定這個的作用中狀態 `ICorDebugBreakpoint` 。|  
|[IsActive 方法](icordebugbreakpoint-isactive-method.md)|取得值，這個值表示這是否 `ICorDebugBreakpoint` 為使用中。|  
  
## <a name="remarks"></a>備註  

 中斷點不會直接支援條件運算式。 如果需要這類功能，偵錯工具必須在上執行 `ICorDebugBreakpoint` 。  
  
 ICorDebugFunctionBreakpoint 介面會擴充 `ICorDebugBreakpoint` 以支援函式內的中斷點。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
