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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 576fb8632818a6b8ffc3e2c0acc50eaafd074de3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766961"
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
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|表示預設呼叫慣例。|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|指出此方法會採用不同數量的參數。|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|表示呼叫的欄位。|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|表示要區域方法呼叫。|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|表示呼叫的屬性。|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|表示 unmanaged 呼叫。|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|表示泛型方法具現化。|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|表示 64 位元的 PInvoke 呼叫接受可變數目之參數的方法。|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|描述無效的 4 位元值。|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|指出，最後四個位元所描述的呼叫慣例。|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|表示的最上層的位元描述`this`參數。|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|表示`this`參數是明確地描述簽章中。|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|表示泛型方法簽章，以明確的型別引數數目。 這在之前的一般參數計數。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
