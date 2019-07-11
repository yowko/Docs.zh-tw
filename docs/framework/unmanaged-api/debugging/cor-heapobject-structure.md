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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a236103b8ca1501ae4c9109c1fd9e78865ab9c9c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740597"
---
# <a name="corheapobject-structure"></a>COR_HEAPOBJECT 結構
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
  
|成員|描述|  
|------------|-----------------|  
|`address`|在記憶體中物件的位址。|  
|`size`|物件，以位元組為單位的大小總計。|  
|`type`|A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)語彙基元，表示物件的型別。|  
  
## <a name="remarks"></a>備註  
 `COR_HEAPOBJECT` 可以擷取執行個體列舉[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)填入藉由呼叫的介面物件[ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)方法。  
  
 A`COR_HEAPOBJECT`執行個體會提供有關在 managed 堆積中，即時物件或物件不根目錄的任何物件，但尚未收集記憶體回收行程的相關資訊。  
  
 為了達到最佳效能，`COR_HEAPOBJECT.address`欄位是`CORDB_ADDRESS`值，而不是 ICorDebugValue 介面中大部分的偵錯 API 所使用的值。 若要取得 ICorDebugValue 物件指定的物件位址，您可以傳遞`CORDB_ADDRESS`值加入[ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)方法。  
  
 為了達到最佳效能，`COR_HEAPOBJECT.type`欄位是`COR_TYPEID`值，而不是 ICorDebugType 介面中大部分的偵錯 API 所使用的值。 若要取得 ICorDebugType 物件指定的型別 id，您可以傳遞`COR_TYPEID`值加入[ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)方法。  
  
 `COR_HEAPOBJECT`結構包含的參考計數的 COM 介面。 如果您擷取`COR_HEAPOBJECT`來自列舉值，藉由呼叫的執行個體[icordebugheapenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)方法，接下來，您必須釋放參考。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
