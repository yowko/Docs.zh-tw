---
title: ICLRHostBindingPolicyManager::EvaluatePolicy 方法
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e37d56a321e6529812045e37c4f1929818b38a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a>ICLRHostBindingPolicyManager::EvaluatePolicy 方法
代表主機評估繫結原則。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pwzReferenceIdentity`  
 [in]之前的原則評估的組件的參考。  
  
 `pbApplicationPolicy`  
 [in]包含原則的資料緩衝區的指標。  
  
 `cbAppPolicySize`  
 [in]大小`pbApplicationPolicy`緩衝區。  
  
 `pwzPostPolicyReferenceIdentity`  
 [out]新的原則資料評估後的組件的參考。  
  
 `pcchPostPolicyReferenceIdentity`  
 [in、 out]新的原則資料評估後的組件識別參考緩衝區大小的指標。  
  
 `pdwPoliciesApplied`  
 [out]指標的邏輯 OR 組合[EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md)值，表示已套用的原則。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成評估。|  
|E_INVALIDARG|可能是`pwzReferenceIdentity`或`pbApplicationPolicy`為 null 參考。|  
|ERROR_INSUFFICIENT_BUFFER|`cbAppPolicySize` 為太小。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `EvaluatePolicy`方法可讓主機來維護主機特定的組件繫結原則會影響版本控制需求。 原則引擎本身會維持在 CLR 中。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRHostBindingPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
