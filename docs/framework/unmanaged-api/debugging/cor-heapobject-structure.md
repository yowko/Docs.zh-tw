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
ms.openlocfilehash: 54af02b48dabdf2042763954805f0d454323ac89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726362"
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
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`address`|記憶體中物件的位址。|  
|`size`|物件的總大小（以位元組為單位）。|  
|`type`|表示物件類型的 [COR_TYPEID](cor-typeid-structure.md) token。|  
  
## <a name="remarks"></a>備註  

 `COR_HEAPOBJECT` 藉由列舉 [ICorDebugHeapEnum](icordebugheapenum-interface.md) 介面物件（藉由呼叫 [ICorDebugProcess5：： EnumerateHeap](icordebugprocess5-enumerateheap-method.md) 方法來填入），即可抓取實例。  
  
 `COR_HEAPOBJECT`實例會針對 managed 堆積上的即時物件，或關於未由垃圾收集行程收集但尚未收集之物件的物件，提供相關資訊。  
  
 為了獲得更好的效能，此 `COR_HEAPOBJECT.address` 欄位是一個 `CORDB_ADDRESS` 值，而非許多偵錯工具 API 中使用的 ICorDebugValue 介面值。 若要取得指定物件位址的 ICorDebugValue 物件，您可以將值傳遞 `CORDB_ADDRESS` 至 [ICorDebugProcess5：： GetObject](icordebugprocess5-getobject-method.md) 方法。  
  
 為了獲得更好的效能，此 `COR_HEAPOBJECT.type` 欄位是一個 `COR_TYPEID` 值，而非許多偵錯工具 API 中使用的 ICorDebugType 介面值。 若要取得給定類型識別碼的 ICorDebugType 物件，您可以將值傳遞 `COR_TYPEID` 至 [ICorDebugProcess5：： GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) 方法。  
  
 `COR_HEAPOBJECT`結構包含參考計數的 COM 介面。 如果您藉 `COR_HEAPOBJECT` 由呼叫 [ICorDebugHeapEnum：： Next](icordebugheapenum-next-method.md) 方法從列舉值取出實例，則必須接著釋放參考。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
