---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
ms.openlocfilehash: 443acfa77dc8103008263f19bed116d02e7ea676
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716716"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a>ICLRAssemblyIdentityManager::GetBindingIdentityFromFile 方法

取得位於指定檔案路徑之元件的元件識別系結資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>參數  

 `pwzFilePath`  
 在要評估之檔案的路徑。  
  
 `dwFlags`  
 在 [ECLRAssemblyIdentityFlags](eclrassemblyidentityflags-enumeration.md) 列舉的值，表示元件的身分識別類型。 提供給未來的擴充性。 CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是 common language runtime (CLR) 2.0 版所支援的唯一值。  
  
 `pwzBuffer`  
 擴展包含不透明元件身分識別資料的緩衝區。  
  
 `pcchBufferSize`  
 [in，out]大小的指標 `pwzBuffer` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|此方法已成功傳回。|  
|E_INVALIDARG|提供的 `pwzFilePath` 是 null。|  
|ERROR_INSUFFICIENT_BUFFER|的大小 `pwzBuffer` 太小。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 `GetBindingIdentityFromFile` 通常會呼叫兩次。 第一個呼叫會為提供 null 值 `pwzBuffer` ，而此方法會在中傳回適當的大小 `pcchBufferSize` 。 第二個呼叫會提供適當配置的緩衝區，而此方法會在完成時傳回實際的緩衝區資料。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyIdentityManager 介面](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [ICLRHostBindingPolicyManager 介面](iclrhostbindingpolicymanager-interface.md)
