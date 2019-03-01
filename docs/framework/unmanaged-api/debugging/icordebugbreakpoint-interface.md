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
ms.openlocfilehash: a7e454c15ddfa977a6d06921a5d80a6c05dca92f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973570"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint 介面

表示函式或在值上的監看點的中斷點。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Activate 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|設定作用中的狀態，這個`ICorDebugBreakpoint`。|  
|[IsActive 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|取得值，指出是否此`ICorDebugBreakpoint`作用中。|  
  
## <a name="remarks"></a>備註  
 中斷點不直接支援條件式運算式。 如果需要這類功能，則偵錯工具必須實作它的上方`ICorDebugBreakpoint`。  
  
 ICorDebugFunctionBreakpoint 介面會擴充`ICorDebugBreakpoint`支援函式內的中斷點。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
