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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf1be8d5c709f3d6e5991e4d33dde2e923291a95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569410"
---
# <a name="corsetenc-enumeration"></a>CorSetENC 列舉
包含值，可用來在中繼資料產生期間影響行為。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`MDUpdateENC`|表示可以更新中繼資料，而不移動語彙基元。|  
|`MDUpdateFull`|表示可以在更新過程中移動語彙基元。|  
|`MDUpdateExtension`|指出，更新可以只包含加入項目。 無法移動語彙基元。|  
|`MDUpdateIncremental`|表示累加編譯。|  
|`MDUpdateDelta`|表示應該儲存，只有已變更的中繼資料。|  
|`MDUpdateMask`|包含`MDUpdateENC`，`MDUpdateFull`和`MDUpdateIncremental`。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
