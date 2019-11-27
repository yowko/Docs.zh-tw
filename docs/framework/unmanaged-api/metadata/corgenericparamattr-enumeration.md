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
ms.openlocfilehash: e4abf876681d5b04555c9f030a94b722874e326e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450288"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr 列舉
包含值，描述泛型型別的 <xref:System.Type> 參數，如[IMetaDataEmit2：:D efinegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)的呼叫中所使用。  
  
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`gpVarianceMask`|參數變異數僅適用于介面和委派的泛型參數。|  
|`gpNonVariant`|表示缺少變異數。|  
|`gpCovariant`|表示共變數。|  
|`gpContravariant`|表示逆變性。|  
|`gpSpecialConstraintMask`|特殊條件約束可以套用至任何 <xref:System.Type> 參數。|  
|`gpNoSpecialConstraint`|表示不會對 <xref:System.Type> 參數套用任何條件約束。|  
|`gpReferenceTypeConstraint`|表示 <xref:System.Type> 參數必須是參考型別。|  
|`gpNotNullableValueTypeConstraint`|表示 <xref:System.Type> 參數必須是不能為 null 值的實值型別。|  
|`gpDefaultConstructorConstraint`|表示 <xref:System.Type> 參數必須具有不採用任何參數的預設公用函式。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
