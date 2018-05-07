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
ms.openlocfilehash: d48d8e7b699f411ec45cf1b5d9810c23583b045e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions 方法
取得 managed 堆積的記憶體範圍的列舉值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppRegions`  
 [out]位址指標[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)介面物件的物件位於 managed 堆積中的記憶體範圍的列舉值。  
  
## <a name="remarks"></a>備註  
 然後再呼叫`ICorDebugProcess5::EnumerateHeapRegions`方法，您應該呼叫[icordebugprocess5:: Getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)方法，並檢查的值`areGCStructuresValid`欄位傳回[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)若要確保記憶體回收堆積中目前的狀態是可列舉物件。 此外，`ICorDebugProcess5::EnumerateHeapRegions`方法會傳回`E_FAIL`附加過早在程序的存留期時，如果之前的記憶體區域建立。  
  
 這個方法保證來列舉所有可能會包含受管理的物件的記憶體區域，但是它並不保證 managed 的物件實際位於這些區域。 [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)集合物件可能包含空白或保留的記憶體區域。  
  
 [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)介面的物件是衍生自 ICorDebugEnum 介面，可讓您列舉的標準列舉值[COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)物件。 每個[COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)物件提供的特定區段，以及該區段中的物件層代的記憶體範圍的相關資訊。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugProcess5 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
