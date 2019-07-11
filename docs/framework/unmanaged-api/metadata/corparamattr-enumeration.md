---
title: CorParamAttr 列舉
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bfa8f1b5df76c7fdfe2f25b637b157bfa4424f7a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781660"
---
# <a name="corparamattr-enumeration"></a>CorParamAttr 列舉
包含值，這些值描述方法參數的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`pdIn`|指定此參數會傳遞至方法呼叫。|  
|`pdOut`|指定參數傳遞從方法傳回。|  
|`pdOptional`|指定的參數為選擇性。|  
|`pdReservedMask`|保留供內部使用的 common language runtime。|  
|`pdHasDefault`|指定參數有預設值。|  
|`pdHasFieldMarshal`|指定參數的封送處理資訊。|  
|`pdUnused`|未使用。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
