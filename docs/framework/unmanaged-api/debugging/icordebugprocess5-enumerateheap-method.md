---
title: ICorDebugProcess5::EnumerateHeap 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: 22ab29f8a204a4b27dafdefcd3652cc3dcf9769c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671131"
---
# <a name="icordebugprocess5enumerateheap-method"></a>ICorDebugProcess5::EnumerateHeap 方法

取得 managed 堆積上物件的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppObject`  
 擴展 [ICorDebugHeapEnum](icordebugheapenum-interface.md) 介面物件位址的指標，該物件是位於 managed 堆積上之物件的列舉值。  
  
## <a name="remarks"></a>備註  

 在呼叫 `ICorDebugProcess5::EnumerateHeap` 方法之前，您應該呼叫 [ICorDebugProcess5：： GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) 方法，並檢查 `areGCStructuresValid` 傳回之 [COR_HEAPINFO](cor-heapinfo-structure.md) 物件的欄位值，以確定處於目前狀態的垃圾收集堆積是可列舉的。 此外， `ICorDebugProcess5::EnumerateHeap` `E_FAIL` 如果您在進程的存留期過早附加，則會在處理 managed 堆積的記憶體之前，傳回。  
  
 [ICorDebugHeapEnum](icordebugheapenum-interface.md)介面物件是衍生自 ICorDebugEnum 介面的標準列舉值，可讓您列舉[COR_HEAPOBJECT](cor-heapobject-structure.md)物件。 這個方法會以提供所有物件相關資訊的[COR_HEAPOBJECT](cor-heapobject-structure.md)實例填入[ICorDebugHeapEnum](icordebugheapenum-interface.md)集合物件。 集合也可能包含 [COR_HEAPOBJECT](cor-heapobject-structure.md) 的實例，這些實例會提供未由任何物件（但垃圾收集行程尚未收集）之物件的相關資訊。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess5 介面](icordebugprocess5-interface.md)
- [偵錯介面](debugging-interfaces.md)
