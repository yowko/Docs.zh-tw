---
title: ICorDebugThread3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 015d0061e5be5bbc212243ca06f1d165abe4496a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729300"
---
# <a name="icordebugthread3-interface"></a>ICorDebugThread3 介面

提供 [ICorDebugStackWalk](icordebugstackwalk-interface.md) 和對應介面的進入點。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateStackWalk 方法](icordebugthread3-createstackwalk-method.md)|為您想要回溯其堆疊的執行緒建立 [ICorDebugStackWalk](icordebugstackwalk-interface.md) 物件。|  
|[GetActiveInternalFrames 方法](icordebugthread3-getactiveinternalframes-method.md)|傳回內部框架的陣列， (堆疊上) 的 [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) 物件。|  
  
## <a name="remarks"></a>備註  

 `ICorDebugThread3` 是 ICorDebugThread 介面的邏輯擴充。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
