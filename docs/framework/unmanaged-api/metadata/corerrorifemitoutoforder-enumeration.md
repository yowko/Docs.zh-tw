---
title: CorErrorIfEmitOutOfOrder 列舉
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
ms.openlocfilehash: 1d1b0cbb8be33f285b63e7353da973455e0fd752
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718848"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder 列舉

包含旗標值，這些值表示中繼資料未按順序發出時，在哪些條件下應該產生錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|指出不會產生錯誤訊息的預設行為。|  
|`MDErrorOutOfOrderNone`|指出編譯器不應產生錯誤訊息。|  
|`MDErrorOutOfOrderAll`|指出當欄位、屬性、事件、方法或參數未按順序發出時，編譯器應該產生錯誤訊息。|  
|`MDMethodOutOfOrder`|指出當方法未按順序發出時，編譯器應該產生錯誤訊息。|  
|`MDFieldOutOfOrder`|指出當欄位未按順序發出時，編譯器應該產生錯誤訊息。|  
|`MDParamOutOfOrder`|指出當參數以順序發出時，編譯器應該產生錯誤訊息。|  
|`MDPropertyOutOfOrder`|指出當屬性以順序發出時，編譯器應該產生錯誤訊息。|  
|`MDEventOutOfOrder`|指出當事件不按順序發出時，編譯器應該產生錯誤訊息。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
