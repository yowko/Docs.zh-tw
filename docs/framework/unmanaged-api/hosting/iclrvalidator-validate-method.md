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
ms.openlocfilehash: 4ce50f7706583f291d2e6a141d40ab6dd3e4b3e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674381"
---
# <a name="iclrvalidatorvalidate-method"></a>ICLRValidator::Validate 方法

在指定的檔案中驗證可攜式可執行檔 (PE) 或 Microsoft 中繼語言 (MSIL) 。  
  
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
 在 `IVEHandler` 處理驗證錯誤之實例的指標。  
  
 `ulAppDomainId`  
 在目前的識別碼 <xref:System.AppDomain> 。  
  
 `ulFlags`  
 在 [ValidatorFlags](validatorflags-enumeration.md) 值的組合，表示應該執行的驗證類型。  
  
 `ulMaxError`  
 在結束驗證之前允許的錯誤數目上限。  
  
 `token`  
 在閒置。  
  
 `fileName`  
 在要驗證之檔案的名稱。  
  
 `pe`  
 在檔案緩衝區的指標。  
  
 `ulSize`  
 在要驗證之檔案的大小（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`Validate` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** IValidator .idl、IValidator。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRValidator 介面](iclrvalidator-interface.md)
