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
ms.openlocfilehash: efb3d913e1d8ef0c486d7e5e1d9777ae7d88bc71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179328"
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
|`type`|表示物件類型的[COR_TYPEID](cor-typeid-structure.md)權杖。|  
  
## <a name="remarks"></a>備註  
 `COR_HEAPOBJECT`可以通過枚舉[ICorDebugHeapEnum](icordebugheapenum-interface.md)介面物件來檢索實例，該介面物件通過調用[ICorDebugProcess5：：：枚舉堆](icordebugprocess5-enumerateheap-method.md)方法填充。  
  
 實例`COR_HEAPOBJECT`提供有關託管堆上的即時物件的資訊，或者提供有關未由任何物件紮根但尚未由垃圾回收器收集的物件的資訊。  
  
 為了更好的性能，該`COR_HEAPOBJECT.address`欄位是一`CORDB_ADDRESS`個值，而不是許多調試 API 中使用的 ICorDebugValue 介面值。 要獲取給定物件位址的 ICorDebugValue 物件，可以將`CORDB_ADDRESS`該值傳遞給[ICorDebugProcess5：：：getObject](icordebugprocess5-getobject-method.md)方法。  
  
 為了更好的性能，該`COR_HEAPOBJECT.type`欄位是一`COR_TYPEID`個值，而不是許多調試 API 中使用的 ICorDebugType 介面值。 要獲取給定類型 ID 的 ICorDebugType 物件，可以將`COR_TYPEID`該值傳遞給[ICorDebugProcess5：：getTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md)方法。  
  
 該`COR_HEAPOBJECT`結構包括一個引用計數的COM介面。 如果通過調用`COR_HEAPOBJECT`[ICorDebugHeapEnum：Next](icordebugheapenum-next-method.md)方法從枚舉器檢索實例，則必須隨後釋放引用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
