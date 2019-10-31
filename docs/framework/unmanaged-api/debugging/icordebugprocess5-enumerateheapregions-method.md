---
title: ICorDebugProcess5::EnumerateHeapRegions 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
ms.openlocfilehash: 3ab4da3fcf43731587dae6f3a8e82ea48c5ee1ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129635"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions 方法
取得 managed 堆積記憶體範圍的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppRegions`  
 脫銷[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)介面物件之位址的指標，這是物件位於 managed 堆積中的記憶體範圍的列舉值。  
  
## <a name="remarks"></a>備註  
 在呼叫 `ICorDebugProcess5::EnumerateHeapRegions` 方法之前，您應該呼叫[ICorDebugProcess5：： GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)方法，並檢查所傳回之[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)物件的 `areGCStructuresValid` 欄位值，以確保其中的垃圾收集堆積目前的狀態是可列舉的。 此外，如果您在進程的存留期間過早附加記憶體區域，則 `ICorDebugProcess5::EnumerateHeapRegions` 方法會傳回 `E_FAIL`。  
  
 這個方法一定會列舉可能包含 managed 物件的所有記憶體區域，但不保證 managed 物件實際上位於這些區域中。 [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)集合物件可能包含空的或保留的記憶體區域。  
  
 [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)介面物件是衍生自 ICorDebugEnum 介面的標準列舉值，可讓您列舉[COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)物件。 每個[COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)物件都會提供特定區段之記憶體範圍的相關資訊，以及該區段中的物件產生。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess5 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
