---
title: COR_FIELD 結構
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
ms.openlocfilehash: ae8e907d0e0d6ef5030b3e9aa1f1b3dcef50193e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726622"
---
# <a name="cor_field-structure"></a>COR_FIELD 結構

提供物件中欄位的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`token`|`mdFieldDef`可以用來取得欄位資訊的權杖。|  
|`offset`|物件中欄位資料的位移（以位元組為單位）。|  
|`id`|識別此欄位之類型的 [COR_TYPEID](cor-typeid-structure.md) 值。|  
|`fieldType`|表示欄位類型的 CorElementType 列舉值。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
