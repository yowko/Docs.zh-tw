---
title: CLR_DEBUGGING_VERSION 結構
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4528ccd77fed2ea2a9b2d08243ffa1535bfad1ae
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274080"
---
# <a name="clr_debugging_version-structure"></a>CLR_DEBUGGING_VERSION 結構
定義用來偵錯之工具通用語言執行平台 (CLR) 的產品版本。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`wStructVersion`|結構版本號碼|  
|`wMajor`|主要版本號碼。|  
|`wMinor`|次要版本號碼。|  
|`wBuild`|組建編號。|  
|`wRevision`|修訂編號。|  
  
## <a name="remarks"></a>備註  
 結構與 COR_VERSION 結構相同，不過`CLR_DEBUGGING_VERSION` ，結構會提供其他結構版本欄位（`wStructVersion`）。 `CLR_DEBUGGING_VERSION` 目前，此欄位必須設定為零。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
