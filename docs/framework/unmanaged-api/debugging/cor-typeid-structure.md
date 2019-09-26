---
title: COR_TYPEID 結構
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d76fa4b2352da18b5ef0e547ebc4e2e99d980b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273988"
---
# <a name="cor_typeid-structure"></a>COR_TYPEID 結構
包含類型識別項。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`token1`|第一個 token。|  
|`token2`|第二個 token。|  
  
## <a name="remarks"></a>備註  
 `COR_TYPEID`結構會由數個偵錯工具傳回，這些方法會提供要進行垃圾收集之物件的相關資訊。 然後，可以將它當做引數傳遞給其他的偵錯工具方法，以提供該專案的其他相關資訊。 例如，藉由列舉[ICorDebugHeapEnum](icordebugheapenum-interface.md)物件，您可以在 managed 堆積上，抓取代表個別物件的個別[COR_HEAPOBJECT](cor-heapobject-structure.md)物件。 接著，您可以將`COR_TYPEID` `COR_HEAPOBJECT.type`欄位中的值傳遞給[ICorDebugProcess5：： GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md)方法，以抓取提供物件之型別資訊的 ICorDebugType 物件。  
  
 `COR_TYPEID`物件應為不透明。 其個別欄位不應存取或操作。 其唯一用途就是當做方法呼叫中的`out`參數提供的識別碼，然後可以傳遞給其他方法來提供其他資訊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
