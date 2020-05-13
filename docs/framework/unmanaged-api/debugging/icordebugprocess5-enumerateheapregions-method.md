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
ms.openlocfilehash: 50b0859d6727a25906f2c8b0f3fe96da228ab886
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213552"
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
 脫銷[ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)介面物件之位址的指標，這是物件位於 managed 堆積中的記憶體範圍的列舉值。  
  
## <a name="remarks"></a>備註  
 呼叫方法之前 `ICorDebugProcess5::EnumerateHeapRegions` ，您應該呼叫[ICorDebugProcess5：： GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md)方法，並檢查 `areGCStructuresValid` 所傳回[COR_HEAPINFO](cor-heapinfo-structure.md)物件之欄位的值，以確保其目前狀態中的垃圾收集堆積是可列舉的。 此外， `ICorDebugProcess5::EnumerateHeapRegions` `E_FAIL` 如果您在進程的存留期間內過早附加，則在建立記憶體區域之前，方法會傳回。  
  
 這個方法一定會列舉可能包含 managed 物件的所有記憶體區域，但不保證 managed 物件實際上位於這些區域中。 [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)集合物件可能包含空的或保留的記憶體區域。  
  
 [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)介面物件是衍生自 ICorDebugEnum 介面的標準列舉值，可讓您列舉[COR_SEGMENT](cor-segment-structure.md)物件。 每個[COR_SEGMENT](cor-segment-structure.md)物件都會提供特定區段之記憶體範圍的相關資訊，以及該區段中的物件產生。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess5 介面](icordebugprocess5-interface.md)
- [偵錯介面](debugging-interfaces.md)
