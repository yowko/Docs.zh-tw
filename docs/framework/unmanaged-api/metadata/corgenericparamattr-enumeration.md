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
ms.openlocfilehash: ea50430c3ae6cef9b47880bcb8ad969f62ce9c39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704906"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr 列舉

包含值，這些值會描述 <xref:System.Type> 泛型型別的參數，如同用在 [IMetaDataEmit2：:D efinegenericparam](imetadataemit2-definegenericparam-method.md)的呼叫中。  
  
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
  
|member|描述|  
|------------|-----------------|  
|`gpVarianceMask`|參數變異數只適用于介面和委派的泛型參數。|  
|`gpNonVariant`|指出沒有變異數。|  
|`gpCovariant`|表示共變數。|  
|`gpContravariant`|表示反變數。|  
|`gpSpecialConstraintMask`|特殊條件約束可以套用至任何 <xref:System.Type> 參數。|  
|`gpNoSpecialConstraint`|指出沒有任何條件約束適用于 <xref:System.Type> 參數。|  
|`gpReferenceTypeConstraint`|指出 <xref:System.Type> 參數必須是參考型別。|  
|`gpNotNullableValueTypeConstraint`|指出 <xref:System.Type> 參數必須是不能是 null 值的實值型別。|  
|`gpDefaultConstructorConstraint`|指出 <xref:System.Type> 參數必須有不採用任何參數的預設公用函數。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
