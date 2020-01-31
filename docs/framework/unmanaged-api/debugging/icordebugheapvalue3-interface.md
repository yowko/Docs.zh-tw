---
title: ICorDebugHeapValue3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
ms.openlocfilehash: ddfe8cee8fdbca910ffa4f6989b1359ae5f7b11f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794375"
---
# <a name="icordebugheapvalue3-interface"></a>ICorDebugHeapValue3 介面
公開物件的監視器鎖定屬性。 這個介面會擴充 ICorDebugHeapValue 和 ICorDebugHeapValue2 介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetThreadOwningMonitorLock 方法](icordebugheapvalue3-getthreadowningmonitorlock-method.md)|傳回擁有這個物件之監視器鎖定的 managed 執行緒。|  
|[GetMonitorEventWaitList 方法](icordebugheapvalue3-getmonitoreventwaitlist-method.md)|提供在與監視器鎖定相關聯的事件上排入佇列之執行緒的已排序清單。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
