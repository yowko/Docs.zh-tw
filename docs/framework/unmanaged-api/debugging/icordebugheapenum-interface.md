---
title: ICorDebugHeapEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: bed2871c46712490bc4b0520fa1ab8023dbab5cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794429"
---
# <a name="icordebugheapenum-interface"></a>ICorDebugHeapEnum 介面
為 Managed 堆積上的物件提供列舉值。 這個介面是 ICorDebugEnum 介面的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Next 方法](icordebugheapenum-next-method.md)|取得指定的[COR_HEAPOBJECT](cor-heapobject-structure.md)實例數目，其中包含 managed 堆積上物件的相關資訊。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugHeapEnum` 介面會執行 ICorDebugEnum 介面。  
  
 `ICorDebugHeapEnum` 實例會藉由呼叫[ICorDebugProcess5：： EnumerateHeap](icordebugprocess5-enumerateheap-method.md)方法來填入[COR_HEAPOBJECT](cor-heapobject-structure.md)實例。 集合中的每個[COR_HEAPOBJECT](cor-heapobject-structure.md)實例都代表堆積上的即時物件，或是未受垃圾收集行程回收但尚未收集的物件。 您可以藉由呼叫[ICorDebugHeapEnum：： Next](icordebugheapenum-next-method.md)方法來列舉集合中的[COR_HEAPOBJECT](cor-heapobject-structure.md)物件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
