---
title: CorGenericParamAttr 列舉
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: ea84b742c901ba58a3bb730f1f5033a0d90610ce
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007373"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr 列舉
包含值，描述 <xref:System.Type> 泛型型別的參數，如同在[IMetaDataEmit2：:D efinegenericparam](imetadataemit2-definegenericparam-method.md)的呼叫中使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`gpVarianceMask`|參數變異數僅適用于介面和委派的泛型參數。|  
|`gpNonVariant`|表示缺少變異數。|  
|`gpCovariant`|表示共變數。|  
|`gpContravariant`|表示逆變性。|  
|`gpSpecialConstraintMask`|特殊條件約束可套用至任何 <xref:System.Type> 參數。|  
|`gpNoSpecialConstraint`|表示不會對參數套用任何條件約束 <xref:System.Type> 。|  
|`gpReferenceTypeConstraint`|表示 <xref:System.Type> 參數必須是參考型別。|  
|`gpNotNullableValueTypeConstraint`|表示 <xref:System.Type> 參數必須是不能為 null 值的實值型別。|  
|`gpDefaultConstructorConstraint`|表示 <xref:System.Type> 參數必須具有不採用任何參數的預設公用函數。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
