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
ms.openlocfilehash: ca2d00611a7530dfb0d1c2a27123947bdf69820d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179345"
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
  
|member|描述|  
|------------|-----------------|  
|`componentID`|陣列包含的物件類型的識別碼。|  
|`componentType`|CorElementType 枚舉值，用於指示元件是垃圾回收引用、值類還是基元。|  
|`firstElementOffset`|陣列中第一個元素的偏移量。|  
|`elementSize`|每個元素的大小。|  
|`countOffset`|陣列中元素數的偏移量。|  
|`rankSize`|排名的大小（以位元組為單位）。|  
|`numRanks`|陣列中的排名數。|  
|`rankOffset`|排名開始的偏移量。|  
  
## <a name="remarks"></a>備註  
 該`rankSize`欄位指定多維陣列中排名的大小。 對於單維陣列來說，它也是準確的。  
  
 對於單維`numRanks`陣列和`N`多維`N`維度陣列，值為 1。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
