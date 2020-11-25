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
ms.openlocfilehash: c9b20500a4a9e4649a938e00e3b059d1395da1d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718926"
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
  
|member|描述|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|表示預設呼叫慣例。|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|指出方法接受參數數目的參數。|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|指出對欄位的呼叫。|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|指出呼叫的是本機方法。|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|指出對屬性的呼叫。|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|表示呼叫未受管理。|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|指出泛型方法具現化。|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|指出採用可變數參數數目之方法的64位 PInvoke 呼叫。|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|描述不正確4位值。|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|指出呼叫慣例是由底部四個位所描述。|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|指出 top 位描述 `this` 參數。|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|指出簽章 `this` 中已明確描述參數。|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|表示具有明確數目之類型引數的泛型方法簽章。 這是在一般的參數計數之前。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
