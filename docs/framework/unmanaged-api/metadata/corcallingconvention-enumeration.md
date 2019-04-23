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
ms.openlocfilehash: 44a4b5903cec2249eb1e176381fe3d8e600dd5e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145869"
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention 列舉
包含值，這些值描述在 Managed 程式碼中進行的呼叫慣例類型。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
