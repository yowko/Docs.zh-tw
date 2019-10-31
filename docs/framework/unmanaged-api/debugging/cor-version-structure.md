---
title: COR_VERSION 結構
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
ms.openlocfilehash: cc9a67e16635209c3bf303e97dc3e5938943a653
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099084"
---
# <a name="cor_version-structure"></a>COR_VERSION 結構
儲存通用語言執行平台的標準四部分版本號碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`dwMajor`|主要版本號碼。|  
|`dwMinor`|次要版本號碼。|  
|`dwBuild`|組建編號。|  
|`dwSubBuild`|子組建編號。|  
  
## <a name="remarks"></a>備註  
 如果版本號碼是1.0.3705.288，1是主要版本號碼，0是次要版本號碼，3705是組建編號，288則是子組建編號。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
