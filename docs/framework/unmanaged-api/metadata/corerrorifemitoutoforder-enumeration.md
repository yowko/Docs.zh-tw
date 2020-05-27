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
ms.openlocfilehash: fec049297bfa12d86cb2a7f7950e84ae540832b1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007426"
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
  
|成員|描述|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|指出預設行為，這不會產生錯誤訊息。|  
|`MDErrorOutOfOrderNone`|表示編譯器不應該產生錯誤訊息。|  
|`MDErrorOutOfOrderAll`|指出當欄位、屬性、事件、方法或參數未按順序發出時，編譯器應該產生錯誤訊息。|  
|`MDMethodOutOfOrder`|指出當方法未按順序發出時，編譯器應該產生錯誤訊息。|  
|`MDFieldOutOfOrder`|指出當欄位未按順序發出時，編譯器應該產生錯誤訊息。|  
|`MDParamOutOfOrder`|指出當參數未按順序發出時，編譯器應該產生錯誤訊息。|  
|`MDPropertyOutOfOrder`|指出當屬性未按順序發出時，編譯器應該產生錯誤訊息。|  
|`MDEventOutOfOrder`|指出當事件未按順序發出時，編譯器應該產生錯誤訊息。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
