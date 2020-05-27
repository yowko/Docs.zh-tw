---
title: CorCallingConvention 列舉
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
ms.openlocfilehash: 310319e8fefe80017c58706e2beaee5eb1e78422
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007898"
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention 列舉
包含值，這些值描述在 Managed 程式碼中進行的呼叫慣例類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|表示預設的呼叫慣例。|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|表示方法會接受可變數目的參數。|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|表示呼叫的是欄位。|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|表示呼叫至區域方法。|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|表示呼叫的是屬性。|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|表示此呼叫未受管理。|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|表示泛型方法具現化。|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|表示對採用可變數目參數的方法進行64位 PInvoke 呼叫。|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|描述不正確4位值。|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|表示呼叫慣例是由下面四個位所描述。|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|表示上位會描述 `this` 參數。|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|表示在簽章 `this` 中明確描述參數。|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|表示具有明確數目之類型引數的泛型方法簽章。 這會優先于一般參數計數。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
