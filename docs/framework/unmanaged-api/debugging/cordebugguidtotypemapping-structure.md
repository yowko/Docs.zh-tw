---
title: CorDebugGuidToTypeMapping 結構
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
ms.openlocfilehash: 859853521b741f42f1de7921de813941d2501173
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729092"
---
# <a name="cordebugguidtotypemapping-structure"></a>CorDebugGuidToTypeMapping 結構

將 Windows 執行階段 GUID 對應至其相對應的 ICorDebugType 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`iid`|快取之 Windows 執行階段類型的 GUID。|  
|`pType`|ICorDebugType 物件的指標，提供快取類型的相關資訊。|  
  
## <a name="requirements"></a>需求  

 **平臺：** Windows 執行階段。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
