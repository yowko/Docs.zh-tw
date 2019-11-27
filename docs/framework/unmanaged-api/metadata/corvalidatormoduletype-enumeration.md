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
ms.openlocfilehash: a8dc09ee9f0f0fd79060bb86c599ab40a285153b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448755"
---
# <a name="corvalidatormoduletype-enumeration"></a>CorValidatorModuleType 列舉
指定模組的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|模組是不正確類型。|  
|`ValidatorModuleTypeMin`|`CorValidatorModuleType` 列舉的最小值。|  
|`ValidatorModuleTypePE`|此模組是可移植的可執行檔（PE）。|  
|`ValidatorModuleTypeObj`|模組是 .obj 檔案。|  
|`ValidatorModuleTypeEnc`|模組是「編輯後繼續」偵錯工具會話。|  
|`ValidatorModuleTypeIncr`|模組是以累加方式建立的模組。|  
|`ValidatorModuleTypeMax`|`CorValidatorModuleType` 列舉的最大值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
