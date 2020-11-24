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
ms.openlocfilehash: 5a51670200f8fc8a98ff7b80334253b37c7d89ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671118"
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
 擴展 [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) 介面物件位址的指標，該物件是物件位於 managed 堆積中的記憶體範圍的列舉值。  
  
## <a name="remarks"></a>備註  

 在呼叫 `ICorDebugProcess5::EnumerateHeapRegions` 方法之前，您應該呼叫 [ICorDebugProcess5：： GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) 方法，並檢查 `areGCStructuresValid` 傳回之 [COR_HEAPINFO](cor-heapinfo-structure.md) 物件的欄位值，以確定處於目前狀態的垃圾收集堆積是可列舉的。 此外， `ICorDebugProcess5::EnumerateHeapRegions` `E_FAIL` 如果您在進程的存留期內，在建立記憶體區域之前儘早附加，方法會傳回。  
  
 這種方法保證會列舉所有可能包含 managed 物件的記憶體區域，但不保證受管理物件實際上位於這些區域中。 [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)集合物件可能包含空白或保留的記憶體區域。  
  
 [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)介面物件是衍生自 ICorDebugEnum 介面的標準列舉值，可讓您列舉[COR_SEGMENT](cor-segment-structure.md)物件。 每個 [COR_SEGMENT](cor-segment-structure.md) 物件都會提供特定區段之記憶體範圍的相關資訊，以及該區段中的物件產生。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess5 介面](icordebugprocess5-interface.md)
- [偵錯介面](debugging-interfaces.md)
