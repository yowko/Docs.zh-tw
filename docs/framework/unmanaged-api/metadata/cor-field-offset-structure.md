---
title: COR_FIELD_OFFSET 結構
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
ms.openlocfilehash: 70fb637cd1edf81be140b0e3306e3b0a483653a6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007984"
---
# <a name="cor_field_offset-structure"></a>COR_FIELD_OFFSET 結構
儲存指定欄位的位移 (在類別中)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`ridOfField`|`mdFieldDef`代表欄位的元資料標記。|  
|`ulOffset`|欄位在其類別中的位移。|  
  
## <a name="remarks"></a>備註  
 [IMetaDataImport：： GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)和[IMetaDataEmit：： SetClassLayout](imetadataemit-setclasslayout-method.md)方法接受型別為的參數 `COR_FIELD_OFFSET` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h .h，Corprof.idl .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料結構](metadata-structures.md)
- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
