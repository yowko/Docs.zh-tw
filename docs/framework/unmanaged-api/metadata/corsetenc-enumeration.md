---
title: CorSetENC 列舉
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: 93a194ea72ab894544927cf96304397b7211b5ac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009154"
---
# <a name="corsetenc-enumeration"></a>CorSetENC 列舉
包含值，可用來在中繼資料產生期間影響行為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`MDSetENCOn`|已過時。|  
|`MDSetENCOff`|已過時。|  
|`MDUpdateENC`|表示中繼資料可以更新，而無法移動權杖。|  
|`MDUpdateFull`|表示權杖可在更新期間移動。|  
|`MDUpdateExtension`|指出更新只能包含新增專案。 無法移動權杖。|  
|`MDUpdateIncremental`|表示編譯是累加的。|  
|`MDUpdateDelta`|指出只應儲存已變更的中繼資料。|  
|`MDUpdateMask`|包含 `MDUpdateENC` 、 `MDUpdateFull` 和 `MDUpdateIncremental` 。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
