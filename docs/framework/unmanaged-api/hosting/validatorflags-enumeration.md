---
title: ValidatorFlags 列舉
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
ms.openlocfilehash: d5eb225241f597baf7a0a5584f4aaf8bf8411ea2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009466"
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags 列舉
包含值，指出應該在呼叫[ICLRValidator：： Validate](iclrvalidator-validate-method.md)方法時執行的驗證類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|指定只應驗證可執行檔中的 Microsoft 中繼語言（MSIL）。|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|指定只應驗證可執行檔的格式。|  
|`VALIDATOR_EXTRA_VERBOSE`|指定應該在上執行和報告所有類型的驗證。|  
|`VALIDATOR_NOCHECK_PEFORMAT`|指定不應驗證可執行檔的格式。|  
|`VALIDATOR_SHOW_SOURCE_LINES`|指定驗證錯誤訊息應包含引發驗證錯誤的源程式碼。 此域值在 .NET Framework 版本2.0 中無效。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** IValidator .idl，IValidator。h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRErrorReportingManager 介面](iclrerrorreportingmanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
