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
ms.openlocfilehash: e9c9674bfe0e5a8006a4881e103b633ee8f2af1d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706044"
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType 列舉

指定由 common language runtime 序列化物件的方式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
|member|描述|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|未定義物件的序列化。|  
|`SERIALIZATION_TYPE_BOOLEAN`|物件序列化為布林類型|  
|`SERIALIZATION_TYPE_CHAR`|物件會序列化為字元類型。|  
|`SERIALIZATION_TYPE_I1`|物件會序列化為帶正負號的1位元組整數。|  
|`SERIALIZATION_TYPE_U1`|物件會序列化為不帶正負號的1位元組整數。|  
|`SERIALIZATION_TYPE_I2`|物件會序列化為帶正負號的2位元組整數。|  
|`SERIALIZATION_TYPE_U2`|物件會序列化為不帶正負號的2位元組整數。|  
|`SERIALIZATION_TYPE_I4`|物件會序列化為帶正負號的4位元組整數。|  
|`SERIALIZATION_TYPE_U4`|物件會序列化為不帶正負號的4位元組整數。|  
|`SERIALIZATION_TYPE_I8`|物件會序列化為帶正負號的8位元組整數。|  
|`SERIALIZATION_TYPE_U8`|物件會序列化為不帶正負號的8位元組整數。|  
|`SERIALIZATION_TYPE_R4`|物件會序列化為4位元組浮點數。|  
|`SERIALIZATION_TYPE_R8`|物件會序列化為8位元組浮點數。|  
|`SERIALIZATION_TYPE_STRING`|物件會序列化為 System.string 類型。|  
|`SERIALIZATION_TYPE_SZARRAY`|物件會序列化為一維、零下限的陣列。|  
|`SERIALIZATION_TYPE_TYPE`|物件會序列化為泛型型別。|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|物件會序列化為加上標籤的物件。|  
|`SERIALIZATION_TYPE_FIELD`|物件會序列化為欄位。|  
|`SERIALIZATION_TYPE_PROPERTY`|物件會序列化為屬性。|  
|`SERIALIZATION_TYPE_ENUM`|物件會序列化為列舉。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
