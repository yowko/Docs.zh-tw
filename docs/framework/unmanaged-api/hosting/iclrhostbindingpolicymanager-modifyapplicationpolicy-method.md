---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy 方法
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178094"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy 方法
修改指定程式集的繫結原則，並創建策略的新版本。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a>參數  
 `pwzSourceAssemblyIdentity`  
 [在]要修改的程式集的標識。  
  
 `pwzTargetAssemblyIdentity`  
 [在]修改程式集的新標識。  
  
 `pbApplicationPolicy`  
 [在]指向緩衝區的指標，其中包含要修改的繫結原則資料。  
  
 `cbAppPolicySize`  
 [在]要替換的繫結原則的大小。  
  
 `dwPolicyModifyFlags`  
 [在][EHostBindingPolicy修改標誌](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md)值的邏輯 OR 組合，指示重定向的控制。  
  
 `pbNewApplicationPolicy`  
 [出]指向包含新繫結原則資料的緩衝區的指標。  
  
 `pcbNewAppPolicySize`  
 [進出]指向新繫結原則緩衝區大小的指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功修改策略。|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity`或`pwzTargetAssemblyIdentity`為空引用。|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` 太小了。|  
|HOST_E_CLRNOTAVAILABLE|公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|調用方不擁有鎖。|  
|HOST_E_ABANDONED|當阻塞的執行緒或光纖等待事件時，事件已被取消。|  
|E_FAIL|發生了未知的災難性故障。 方法返回E_FAIL後，CLR 在進程中不再可用。 對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 該方法`ModifyApplicationPolicy`可以調用兩次。 第一個調用應為`pbNewApplicationPolicy`參數提供 null 值。 此調用將返回，並帶有`pcbNewAppPolicySize`所需的值。 第二個調用應為`pcbNewAppPolicySize`提供此值，並指向 該大小的緩衝區。 `pbNewApplicationPolicy`  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRHostBindingPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
