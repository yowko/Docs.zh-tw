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
ms.openlocfilehash: e32714bba2403752f1ac2551ab182f2655f1fa75
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703851"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy 方法
修改指定元件的系結原則，並建立新版本的原則。  
  
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
 在要修改之元件的識別。  
  
 `pwzTargetAssemblyIdentity`  
 在已修改元件的新識別。  
  
 `pbApplicationPolicy`  
 在緩衝區的指標，其中包含要修改之元件的系結原則資料。  
  
 `cbAppPolicySize`  
 在要取代的系結原則大小。  
  
 `dwPolicyModifyFlags`  
 在[EHostBindingPolicyModifyFlags](ehostbindingpolicymodifyflags-enumeration.md)值的邏輯 OR 組合，表示重新導向的控制權。  
  
 `pbNewApplicationPolicy`  
 脫銷包含新系結原則資料之緩衝區的指標。  
  
 `pcbNewAppPolicySize`  
 [in、out]新系結原則緩衝區大小的指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|已成功修改原則。|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity`或為 `pwzTargetAssemblyIdentity` null 參考。|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` 太小了。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `ModifyApplicationPolicy`方法可以呼叫兩次。 第一個呼叫應該為參數提供 null 值 `pbNewApplicationPolicy` 。 這個呼叫會傳回，而且會傳回的必要值 `pcbNewAppPolicySize` 。 第二個呼叫應該提供這個值給 `pcbNewAppPolicySize` ，並指向該大小的緩衝區 `pbNewApplicationPolicy` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRHostBindingPolicyManager 介面](iclrhostbindingpolicymanager-interface.md)
