---
title: "COR_ARRAY_LAYOUT 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_ARRAY_LAYOUT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_ARRAY_LAYOUT
helpviewer_keywords: COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 02ddd87cfaf16990ff487dfe27f30a2493cb9a01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="corarraylayout-structure"></a>COR_ARRAY_LAYOUT 結構
提供記憶體中陣列物件配置的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
|成員|說明|  
|------------|-----------------|  
|`componentID`|此陣列中包含的物件類型識別項。|  
|`componentType`|CorElementType 列舉值，指出元件是否記憶體回收集合參考、 實值類別或基本型別。|  
|`firstElementOffset`|要在陣列中的第一個元素的位移。|  
|`elementSize`|每個項目的大小。|  
|`countOffset`|要在陣列中的項目數的位移。|  
|`rankSize`|陣序規範，以位元組為單位的大小。|  
|`numRanks`|陣列的排列次序數目。|  
|`rankOffset`|順位的開始位移。|  
  
## <a name="remarks"></a>備註  
 `rankSize`欄位多維陣列中指定的陣序規範的大小。 它是正確的單一維度的陣列。  
  
 值`numRanks`為一維陣列的 1 和`N`多維陣列的`N`維度。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
