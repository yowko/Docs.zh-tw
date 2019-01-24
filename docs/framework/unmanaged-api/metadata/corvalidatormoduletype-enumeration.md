---
title: CorValidatorModuleType 列舉
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee1cfe52caa9d727a132d7adc23b03575293db65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716774"
---
# <a name="corvalidatormoduletype-enumeration"></a>CorValidatorModuleType 列舉
指定模組的類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|此模組是無效的類型。|  
|`ValidatorModuleTypeMin`|最小值`CorValidatorModuleType`列舉。|  
|`ValidatorModuleTypePE`|此模組是可攜式執行檔 (PE) 檔案。|  
|`ValidatorModuleTypeObj`|此模組是.obj 檔。|  
|`ValidatorModuleTypeEnc`|此模組是編輯後繼續偵錯工具工作階段。|  
|`ValidatorModuleTypeIncr`|此模組是以累加方式內建的其中一個。|  
|`ValidatorModuleTypeMax`|最大值`CorValidatorModuleType`列舉。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
