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
ms.openlocfilehash: 313f6649448653ad630d616c7dbf739653e352dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132833"
---
# <a name="cordebugguidtotypemapping-structure"></a>CorDebugGuidToTypeMapping 結構
將 Windows 執行階段的 GUID 對應至其相對應的 ICorDebugType 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`iid`|快取 Windows 執行階段類型的 GUID。|  
|`pType`|ICorDebugType 物件的指標，提供快取類型的相關資訊。|  
  
## <a name="requirements"></a>需求  
 **平臺：** Windows 執行階段。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
