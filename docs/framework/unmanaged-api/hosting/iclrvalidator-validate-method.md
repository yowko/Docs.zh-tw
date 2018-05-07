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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2ad9ef473a498804e5b3ac0469b5b68697c49f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrvalidatorvalidate-method"></a>ICLRValidator::Validate 方法
驗證的可攜式執行檔 (PE) 或 Microsoft 中繼語言 (MSIL)，在指定的檔案。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `veh`  
 [in]指標`IVEHandler`處理驗證錯誤的執行個體。  
  
 `ulAppDomainId`  
 [in]目前的識別項<xref:System.AppDomain>。  
  
 `ulFlags`  
 [in]組合[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)值，表示應該執行的驗證類型。  
  
 `ulMaxError`  
 [in]結束驗證前，允許的錯誤數目上限。  
  
 `token`  
 [in]未使用。  
  
 `fileName`  
 [in]要驗證檔案的名稱。  
  
 `pe`  
 [in]檔案緩衝區的指標。  
  
 `ulSize`  
 [in]以位元組為單位來驗證檔案大小。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`Validate` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 方法會傳回 E_FAIL CLR 已不再可用的處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** IValidator.idl、 IValidator.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRValidator 介面](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
