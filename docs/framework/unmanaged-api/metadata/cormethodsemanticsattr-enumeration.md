---
title: CorMethodSemanticsAttr 列舉
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
ms.openlocfilehash: 347b323951b0125ffa5f82626b2d9b235079492c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676942"
---
# <a name="cormethodsemanticsattr-enumeration"></a>CorMethodSemanticsAttr 列舉

包含值，這些值描述方法與關聯的屬性或事件之間的關聯性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`msSetter`|指定方法為 `set` 屬性的存取子。|  
|`msGetter`|指定方法為 `get` 屬性的存取子。|  
|`msOther`|指定方法具有與屬性的關聯性，或與這裡定義的不同的事件。|  
|`msAddOn`|指定方法加入事件的處理常式方法。|  
|`msRemoveOn`|指定方法移除事件的處理常式方法。|  
|`msFire`|指定方法會引發事件。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
