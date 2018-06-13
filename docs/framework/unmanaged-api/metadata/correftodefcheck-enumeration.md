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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5caf432b5de7cb0c8ff0e6f53b3e79a64ecf802e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443309"
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck 列舉
指定旗標，以控制哪些參考的項目已轉換成其定義，以便最佳化程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`MDRefToDefDefault`|指定參考類型和成員參考應該轉換成定義。 這是預設值 (`MDTypeRefToDef` &#124; `MDMemberRefToDef`)。|  
|`MDRefToDefAll`|指定應該轉換成定義的所有參考的項目。|  
|`MDRefToDefNone`|指定參考的項目應該將轉換成定義。|  
|`MDTypeRefToDef`|指定只有型別參考，應該轉換成的類型定義。|  
|`MDMemberRefToDef`|指定只有成員參考，應該轉換成定義。 也就是成員參考應該轉換方法定義或欄位定義。|  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
