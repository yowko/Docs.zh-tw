---
title: CorNativeLinkType 列舉
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
ms.openlocfilehash: 29f2401e2e3faccae05ca5249fcd7d9e89aacb46
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007607"
---
# <a name="cornativelinktype-enumeration"></a>CorNativeLinkType 列舉
提供值，這些值表示機器碼中已連結的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`nltNone`|指出未指定任何關鍵字。|  
|`nltAnsi`|表示已指定 ANSI 關鍵字。|  
|`nltUnicode`|表示已指定 Unicode 關鍵字|  
|`nltAuto`|表示已指定 auto 關鍵字。|  
|`nltOle`|表示已指定 OLE 關鍵字。|  
|`nltMaxValue`|未使用。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
