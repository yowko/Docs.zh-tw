---
title: "ValidatorFlags 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ValidatorFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ValidatorFlags
helpviewer_keywords: ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f283beb79ec47454185800bd772904c3c696c7c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags 列舉
包含值，表示應該執行的呼叫中的驗證類型[iclrvalidator:: Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|指定應該驗證只的 Microsoft intermediate language (MSIL) 中的可執行檔。|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|指定應該驗證可執行檔的格式。|  
|`VALIDATOR_EXTRA_VERBOSE`|指定應該執行所有類型的驗證及報告。|  
|`VALIDATOR_NOCHECK_PEFORMAT`|指定不驗證可執行檔的格式。|  
|`VALIDATOR_SHOW_SOURCE_LINES`|指定的驗證錯誤訊息應該包括發生驗證錯誤的原始程式碼字行。 .NET Framework 2.0 版中，這個欄位的值無效。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** IValidator.idl、 IValidator.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRErrorReportingManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
