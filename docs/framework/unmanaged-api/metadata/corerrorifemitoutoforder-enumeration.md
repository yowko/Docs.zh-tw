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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4e9d03dcf4603f9470f8f2509050eb6f875746a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442636"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder 列舉
包含旗標值，這些值表示中繼資料未按順序發出時，在哪些條件下應該產生錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`MDErrorOutOfOrderDefault`|表示預設行為，也不會產生錯誤訊息。|  
|`MDErrorOutOfOrderNone`|表示編譯器應該不會產生錯誤訊息。|  
|`MDErrorOutOfOrderAll`|表示編譯器應該產生錯誤訊息，當欄位、 屬性、 事件、 方法或參數，就會發出順序。|  
|`MDMethodOutOfOrder`|表示未按順序發出方法時，編譯器應該產生錯誤訊息。|  
|`MDFieldOutOfOrder`|表示未按順序發出欄位時編譯器應該產生錯誤訊息。|  
|`MDParamOutOfOrder`|表示未按順序發出參數時，編譯器應該產生錯誤訊息。|  
|`MDPropertyOutOfOrder`|表示未按順序發出屬性時，編譯器應該產生錯誤訊息。|  
|`MDEventOutOfOrder`|表示編譯器應該產生錯誤訊息時就會發出事件順序。|  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
