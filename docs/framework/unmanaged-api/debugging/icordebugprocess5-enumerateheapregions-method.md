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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9340977c55c54b9a4683115000293d1c98dfcf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767467"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions 方法
取得 managed 堆積的記憶體範圍的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppRegions`  
 [out]位址指標[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)介面物件，該物件位於 managed 堆積中的記憶體範圍的列舉值物件。  
  
## <a name="remarks"></a>備註  
 然後再呼叫`ICorDebugProcess5::EnumerateHeapRegions`方法，您應該呼叫[ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)方法，並檢查的值`areGCStructuresValid`傳回的欄位[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)若要確保記憶體回收堆積中目前的狀態是可列舉的物件。 颾魤 ㄛ`ICorDebugProcess5::EnumerateHeapRegions`方法會傳回`E_FAIL`附加過早在程序的存留期時，如果之前的記憶體區域建立。  
  
 此方法保證列舉的所有記憶體區域，可能會包含受管理的物件，但它並不保證受管理的物件實際上位於這些區域。 [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)集合物件可能包含空白或保留的記憶體區域。  
  
 [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)介面的物件是衍生自 ICorDebugEnum 介面，可讓您列舉的標準列舉值[COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)物件。 每個[COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)物件提供的特定區段，以及該區段中的物件層代的記憶體範圍的相關資訊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess5 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
