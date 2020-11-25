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
ms.openlocfilehash: 1a8ab5aa5909af60089d5e4cc8092e15bc75e8cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724178"
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
  
|member|描述|  
|------------|-----------------|  
|`ridOfField`|`mdFieldDef`表示欄位的元資料標記。|  
|`ulOffset`|欄位在其類別中的位移。|  
  
## <a name="remarks"></a>備註  

 [IMetaDataImport：： GetClassLayout](imetadataimport-getclasslayout-method.md) 和 [IMetaDataEmit：： SetClassLayout](imetadataemit-setclasslayout-method.md) 方法會採用類型的參數 `COR_FIELD_OFFSET` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h .h、Corprof.h .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料結構](metadata-structures.md)
- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
