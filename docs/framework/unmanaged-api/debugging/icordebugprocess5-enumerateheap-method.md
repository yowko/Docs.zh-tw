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
ms.openlocfilehash: 9386c77cc98df17d797d5886e1603ffc4824b6dc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205241"
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
 脫銷[ICorDebugHeapEnum](icordebugheapenum-interface.md)介面物件之位址的指標，這是位於 managed 堆積上之物件的列舉值。  
  
## <a name="remarks"></a>備註  
 呼叫方法之前 `ICorDebugProcess5::EnumerateHeap` ，您應該呼叫[ICorDebugProcess5：： GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md)方法，並檢查 `areGCStructuresValid` 所傳回[COR_HEAPINFO](cor-heapinfo-structure.md)物件之欄位的值，以確保其目前狀態中的垃圾收集堆積是可列舉的。 此外， `ICorDebugProcess5::EnumerateHeap` `E_FAIL` 如果您在進程的存留期間內過早附加，則會傳回，而在配置受控堆積的記憶體之前。  
  
 [ICorDebugHeapEnum](icordebugheapenum-interface.md)介面物件是衍生自 ICorDebugEnum 介面的標準列舉值，可讓您列舉[COR_HEAPOBJECT](cor-heapobject-structure.md)物件。 這個方法會在[ICorDebugHeapEnum](icordebugheapenum-interface.md)集合物件中填入提供所有物件相關資訊的[COR_HEAPOBJECT](cor-heapobject-structure.md)實例。 此集合也可以包含[COR_HEAPOBJECT](cor-heapobject-structure.md)實例，這些實例會提供未由任何物件（但垃圾收集行程尚未收集）之物件的相關資訊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess5 介面](icordebugprocess5-interface.md)
- [偵錯介面](debugging-interfaces.md)
