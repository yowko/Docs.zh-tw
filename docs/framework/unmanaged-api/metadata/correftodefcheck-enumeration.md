---
title: CorRefToDefCheck 列舉
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: ce6f5993b9c1aeb63e121b3567ee468cea1c9318
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007516"
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck 列舉
指定旗標，以控制哪些參考的項目已轉換成其定義，以便最佳化程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`MDRefToDefDefault`|指定型別參考和成員參考應該轉換成定義。 這是預設值（ `MDTypeRefToDef` &#124; `MDMemberRefToDef` ）。|  
|`MDRefToDefAll`|指定所有參考的專案都應該轉換成定義。|  
|`MDRefToDefNone`|指定不應該將參考的專案轉換成定義。|  
|`MDTypeRefToDef`|指定只有型別參考應該轉換成型別定義。|  
|`MDMemberRefToDef`|指定只應將成員參考轉換成定義。 也就是，成員參考應該轉換成方法定義或欄位定義。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
