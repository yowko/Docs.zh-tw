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
ms.openlocfilehash: 651b916a0e3ca178432094428611f9bcc8f0fd17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132424"
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`wStructVersion`|結構版本號碼|  
|`wMajor`|主要版本號碼。|  
|`wMinor`|次要版本號碼。|  
|`wBuild`|組建編號。|  
|`wRevision`|修訂編號。|  
  
## <a name="remarks"></a>備註  
 `CLR_DEBUGGING_VERSION` 結構與 COR_VERSION 結構相同，不過，`CLR_DEBUGGING_VERSION` 結構會提供額外的結構版本欄位（`wStructVersion`）。 目前，此欄位必須設定為零。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
