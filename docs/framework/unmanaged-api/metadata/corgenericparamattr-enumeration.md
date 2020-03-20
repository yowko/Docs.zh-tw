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
ms.openlocfilehash: bf0008ce9429671f0c156df4256bed0b2aaee184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176171"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr 列舉
包含描述泛型型別的<xref:System.Type>參數的值，如調用[IMetaDataEmit2：:DefinegenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)中使用的。  
  
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
|`gpVarianceMask`|參數方差僅適用于介面和委託的泛型參數。|  
|`gpNonVariant`|指示不存在方差。|  
|`gpCovariant`|表示共變數。|  
|`gpContravariant`|表示不差異。|  
|`gpSpecialConstraintMask`|特殊約束可以應用於任何<xref:System.Type>參數。|  
|`gpNoSpecialConstraint`|指示沒有約束應用於參數<xref:System.Type>。|  
|`gpReferenceTypeConstraint`|指示參數<xref:System.Type>必須是參考型別。|  
|`gpNotNullableValueTypeConstraint`|指示參數<xref:System.Type>必須是不能為空值的數值型別。|  
|`gpDefaultConstructorConstraint`|指示<xref:System.Type>參數必須具有不需要參數的預設公共建構函式。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫德  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
