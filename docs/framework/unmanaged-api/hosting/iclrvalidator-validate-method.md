---
title: ICLRValidator::Validate 方法
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: 427895ffea94e6c657d775ebdeb8571070a61c6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178054"
---
# <a name="iclrvalidatorvalidate-method"></a>ICLRValidator::Validate 方法
驗證指定檔中的可移植可執行 （PE） 或 Microsoft 中間語言 （MSIL）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);
```  
  
## <a name="parameters"></a>參數  
 `veh`  
 [在]指向處理驗證錯誤的`IVEHandler`實例的指標。  
  
 `ulAppDomainId`  
 [在]當前<xref:System.AppDomain>的識別碼。  
  
 `ulFlags`  
 [在][驗證器標誌](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)值的組合，指示應執行的驗證類型。  
  
 `ulMaxError`  
 [在]退出驗證之前要允許的最大錯誤數。  
  
 `token`  
 [在]閒置。  
  
 `fileName`  
 [在]要驗證的檔的名稱。  
  
 `pe`  
 [在]指向檔案緩衝區的指標。  
  
 `ulSize`  
 [在]要驗證的檔的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`Validate`已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|調用方不擁有鎖。|  
|HOST_E_ABANDONED|當阻塞的執行緒或光纖等待事件時，事件已被取消。|  
|E_FAIL|發生了未知的災難性故障。 當方法返回E_FAIL時，CLR 在進程中不再可用。 對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** I 驗證器.idl， I 驗證器.h  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRValidator 介面](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
