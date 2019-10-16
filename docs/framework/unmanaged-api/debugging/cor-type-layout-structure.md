---
title: COR_TYPE_LAYOUT 結構
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bd274b1eb14532629580e777288317186544912
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274169"
---
# <a name="cor_type_layout-structure"></a>COR_TYPE_LAYOUT 結構
提供記憶體中物件配置的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`parentID`|這個類型之父類型的識別碼。 如果類型識別碼對應至<xref:System.Object?displayProperty=nameWithType>，這會是 Null 類型識別碼（token1 = 0，token2 = 0）。|  
|`objectSize`|這個類型之物件的基底大小。 這是非可變大小物件的總大小。|  
|`numFields`|此類型的物件中包含的欄位數目。|  
|`boxOffset`|如果此類型已框出，則為物件欄位的開始位移。 此欄位僅適用于實數值型別，例如基本和結構。|  
|`type`|此類型所屬的 CorElementType。|  
  
## <a name="remarks"></a>備註  
 如果`numFields`大於零，您可以呼叫[ICorDebugProcess5：： GetTypeFields](icordebugprocess5-gettypefields-method.md)方法，以取得有關此類型中欄位的資訊。 如果`type`為`ELEMENT_TYPE_STRING`、`ELEMENT_TYPE_ARRAY` 或，`ELEMENT_TYPE_SZARRAY`則此類型的物件大小為變數，而且您可以將 [COR_TYPEID](cor-typeid-structure.md) 結構傳遞至[ICorDebugProcess5：：GetArrayLayout](icordebugprocess5-getarraylayout-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
