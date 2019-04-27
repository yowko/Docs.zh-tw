---
title: CorSerializationType 列舉
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15b1f6be2dac6bc7566852791ac22e495949521c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992637"
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType 列舉
指定 common language runtime 序列化物件的方式。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|物件序列化為未定義。|  
|`SERIALIZATION_TYPE_BOOLEAN`|將物件序列化為的布林值的類型|  
|`SERIALIZATION_TYPE_CHAR`|物件會序列化為字元類型。|  
|`SERIALIZATION_TYPE_I1`|物件會序列化為帶正負號的 1 位元整數。|  
|`SERIALIZATION_TYPE_U1`|物件會序列化為不帶正負號的 1 位元整數。|  
|`SERIALIZATION_TYPE_I2`|物件會序列化為 2 位元組帶正負號的整數。|  
|`SERIALIZATION_TYPE_U2`|物件會序列化為不帶正負號的 2 位元整數。|  
|`SERIALIZATION_TYPE_I4`|物件會序列化為 4 位元組帶正負號的整數。|  
|`SERIALIZATION_TYPE_U4`|物件會序列化為 4 位元組不帶正負號的整數。|  
|`SERIALIZATION_TYPE_I8`|物件會序列化為帶正負號的 8 位元整數。|  
|`SERIALIZATION_TYPE_U8`|物件會序列化為不帶正負號的 8 位元整數。|  
|`SERIALIZATION_TYPE_R4`|物件會序列化成 4 位元組浮點數。|  
|`SERIALIZATION_TYPE_R8`|物件會序列化為 8 位元組浮點數。|  
|`SERIALIZATION_TYPE_STRING`|將物件序列化為 System.String 類型。|  
|`SERIALIZATION_TYPE_SZARRAY`|將物件序列化為一維，下限為零的陣列。|  
|`SERIALIZATION_TYPE_TYPE`|物件會序列化為泛型型別。|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|物件會序列化為標記的物件。|  
|`SERIALIZATION_TYPE_FIELD`|物件會序列化為欄位。|  
|`SERIALIZATION_TYPE_PROPERTY`|物件會序列化為屬性。|  
|`SERIALIZATION_TYPE_ENUM`|物件會序列化為列舉型別。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
