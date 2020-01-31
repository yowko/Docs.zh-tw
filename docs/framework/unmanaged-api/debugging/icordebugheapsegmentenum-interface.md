---
title: ICorDebugHeapSegmentEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: 98e3351c9c86961d11b0985117259d0ff3b609ae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794412"
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum 介面
為 Managed 堆積的記憶體區域提供列舉值。 這個介面是 ICorDebugEnum 介面的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Next 方法](icordebugheapsegmentenum-next-method.md)|取得指定的[COR_HEAPOBJECT](cor-heapobject-structure.md)實例數目，其中包含 managed 堆積區域的相關資訊。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugHeapSegmentEnum` 介面會執行 ICorDebugEnum 介面。  
  
 `ICorDebugHeapSegmentEnum` 實例會藉由呼叫[ICorDebugProcess5：： EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md)方法來填入[COR_HEAPOBJECT](cor-heapobject-structure.md)實例。 您可以藉由呼叫[ICorDebugHeapSegmentEnum：： Next](icordebugheapsegmentenum-next-method.md)方法來列舉集合中的[COR_HEAPOBJECT](cor-heapobject-structure.md)物件。  
  
 `ICorDebugHeapSegmentEnum` 集合物件會列舉可能包含 managed 物件的所有記憶體區域，但不保證 managed 物件實際上位於這些區域中。 其中可能包含空的或保留的記憶體區域相關資訊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
