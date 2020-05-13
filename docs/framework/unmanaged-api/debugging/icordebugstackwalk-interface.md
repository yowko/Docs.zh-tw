---
title: ICorDebugStackWalk 介面
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
ms.openlocfilehash: 5f71dfcdffaaa683ca4f2abebaa99115ef90e0ff
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378911"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk 介面
提供用來在執行緒堆疊上取得 Managed 方法或框架的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetContext 方法](icordebugstackwalk-getcontext-method.md)|傳回物件中目前框架的內容 `ICorDebugStackWalk` 。|  
|[SetContext 方法](icordebugstackwalk-setcontext-method.md)|將 `ICorDebugStackWalk` 物件的目前內容設定為執行緒的有效內容。|  
|[下一個方法](icordebugstackwalk-next-method.md)|將 `ICorDebugStackWalk` 物件移到下一個框架。|  
|[GetFrame 方法](icordebugstackwalk-getframe-method.md)|取得物件中的目前框架 `ICorDebugStackWalk` 。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
