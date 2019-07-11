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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 981829500e499be05a8de7c1ffb4683429a903e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781852"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr 列舉
包含描述值<xref:System.Type>呼叫中使用的泛型類型參數[IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)。  
  
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
|`gpVarianceMask`|參數的變異數只適用於介面和委派的泛型參數。|  
|`gpNonVariant`|表示變異數不存在。|  
|`gpCovariant`|表示共異變數。|  
|`gpContravariant`|表示反變數。|  
|`gpSpecialConstraintMask`|特殊條件約束可以套用至任何<xref:System.Type>參數。|  
|`gpNoSpecialConstraint`|指出沒有條件約束套用至<xref:System.Type>參數。|  
|`gpReferenceTypeConstraint`|表示<xref:System.Type>參數必須是參考型別。|  
|`gpNotNullableValueTypeConstraint`|表示<xref:System.Type>參數必須是實值類型不得為 null 的值。|  
|`gpDefaultConstructorConstraint`|表示<xref:System.Type>參數必須要有的預設公用建構函式不接受任何參數。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
