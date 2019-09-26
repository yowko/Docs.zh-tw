---
title: COR_ARRAY_LAYOUT 結構
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec9c4f3afb8f3b7e75e22874996d57d29ce8cf16
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274209"
---
# <a name="cor_array_layout-structure"></a>COR_ARRAY_LAYOUT 結構
提供記憶體中陣列物件配置的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;   
    ULONG32 rankSize;   
    ULONG32 numRanks;   
    ULONG32 rankOffset;   
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`componentID`|陣列所包含之物件類型的識別碼。|  
|`componentType`|指出元件是否為垃圾收集參考、實值類別或基本類型的 CorElementType 列舉值。|  
|`firstElementOffset`|陣列中第一個元素的位移。|  
|`elementSize`|每個元素的大小。|  
|`countOffset`|陣列中元素數目的位移。|  
|`rankSize`|順位的大小（以位元組為單位）。|  
|`numRanks`|陣列中的次序數目。|  
|`rankOffset`|排名開始的位移。|  
  
## <a name="remarks"></a>備註  
 `rankSize`欄位會指定多維度陣列中的次序大小。 一維陣列也是正確的。  
  
 針對一維`numRanks`陣列和`N` `N`維度的多維陣列，的值是1。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
