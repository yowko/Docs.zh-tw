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
ms.openlocfilehash: f37bf545553045b9737b7057feed78e1f06ace4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099461"
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
  
## <a name="members"></a>Members  
  
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
 [`rankSize`] 欄位會指定多維度陣列中的次序大小。 一維陣列也是正確的。  
  
 一維陣列的 `numRanks` 值是1，而 `N` 維度的多維陣列則 `N`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
