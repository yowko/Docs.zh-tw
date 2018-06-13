---
title: ICorDebugBreakpoint Interface1
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
ms.openlocfilehash: 220cd1a41ed69325b557e6498a511865b78817ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404511"
---
# <a name="icordebugbreakpoint-interface1"></a>ICorDebugBreakpoint Interface1
表示函式或監看式上的點值中的中斷點。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Activate 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|設定這個的使用中狀態`ICorDebugBreakpoint`。|  
|[IsActive 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|取得值，指出是否此`ICorDebugBreakpoint`為作用中。|  
  
## <a name="remarks"></a>備註  
 中斷點不直接支援條件式運算式。 如果想要使用這類功能，偵錯工具必須實作它最上層的`ICorDebugBreakpoint`。  
  
 ICorDebugFunctionBreakpoint 介面延伸`ICorDebugBreakpoint`支援函式內的中斷點。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
