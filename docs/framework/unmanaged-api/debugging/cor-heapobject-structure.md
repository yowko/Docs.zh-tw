---
title: COR_HEAPOBJECT 結構
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: 270360a8950197eca14e02a60554659e5ac7b91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099071"
---
# <a name="cor_heapobject-structure"></a>COR_HEAPOBJECT 結構
提供 Managed 堆積上的物件相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`address`|記憶體中物件的位址。|  
|`size`|物件的總大小（以位元組為單位）。|  
|`type`|代表物件類型的[COR_TYPEID](cor-typeid-structure.md) token。|  
  
## <a name="remarks"></a>備註  
 藉由列舉藉由呼叫[ICorDebugProcess5：： EnumerateHeap](icordebugprocess5-enumerateheap-method.md)方法填入的[ICorDebugHeapEnum](icordebugheapenum-interface.md)介面物件，可以抓取 `COR_HEAPOBJECT` 實例。  
  
 `COR_HEAPOBJECT` 實例提供有關 managed 堆積上之即時物件的資訊，或關於未由任何物件（但垃圾收集行程尚未收集）的物件。  
  
 為獲得較佳的效能，`COR_HEAPOBJECT.address` 欄位是 `CORDB_ADDRESS` 值，而不是大部分偵錯工具 API 中使用的 ICorDebugValue 介面值。 若要取得指定物件位址的 ICorDebugValue 物件，您可以將 `CORDB_ADDRESS` 值傳遞至[ICorDebugProcess5：： GetObject](icordebugprocess5-getobject-method.md)方法。  
  
 為獲得較佳的效能，`COR_HEAPOBJECT.type` 欄位是 `COR_TYPEID` 值，而不是大部分偵錯工具 API 中使用的 ICorDebugType 介面值。 若要取得給定型別識別碼的 ICorDebugType 物件，您可以將 `COR_TYPEID` 值傳遞至[ICorDebugProcess5：： GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md)方法。  
  
 `COR_HEAPOBJECT` 結構包含參考計數的 COM 介面。 如果您藉由呼叫[ICorDebugHeapEnum：： Next](icordebugheapenum-next-method.md)方法從列舉值抓取 `COR_HEAPOBJECT` 實例，您就必須釋放參考。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
