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
ms.openlocfilehash: 7efb2c3e8033b8bd8fa736a29b2ab9b3bedebeaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109638"
---
# <a name="cortypelayout-structure"></a>COR_TYPE_LAYOUT 結構
提供記憶體中物件配置的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`parentID`|此類型的父類型的識別碼。 這會是 NULL 類型識別碼 (token1 = 0，token2 = 0) 的型別 id 對應於<xref:System.Object?displayProperty=nameWithType>。|  
|`objectSize`|此類型物件的基底的大小。 這是針對非變數大小物件的總大小。|  
|`numFields`|此類型的物件中包含的欄位數目。|  
|`boxOffset`|如果此類型經過 box 處理，則會在物件的欄位的位移開頭。 這個欄位是僅適用於實值型別，例如基本類型和結構。|  
|`type`|CorElementType，屬於此類型。|  
  
## <a name="remarks"></a>備註  
 如果`numFields`是小於或等於零，您可以呼叫[ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)方法，以取得此類型中的欄位的相關資訊。 如果`type`已`ELEMENT_TYPE_STRING`， `ELEMENT_TYPE_ARRAY`，或`ELEMENT_TYPE_SZARRAY`，此類型之物件的大小是變數，您可以傳遞[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)結構[ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
