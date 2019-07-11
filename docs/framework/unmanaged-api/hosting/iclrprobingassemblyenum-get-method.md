---
title: ICLRProbingAssemblyEnum::Get 方法
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3225e42df44e719ecde31c26fae70f26731fa157
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761579"
---
# <a name="iclrprobingassemblyenumget-method"></a>ICLRProbingAssemblyEnum::Get 方法
取得組件識別的指定索引處。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwIndex`  
 [in]要傳回的組件身分識別以零為起始的索引。  
  
 `pwzBuffer`  
 [out]包含組件身分識別資料的緩衝區。  
  
 `pcchBufferSize`  
 [in、 out]大小`pwzBuffer`緩衝區。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|`Get` 已成功傳回。|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` 為太小。|  
|ERROR_NO_MORE_ITEMS|列舉包含的任何其他項目。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。 任何裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 位於索引 0 的身分識別是特有的處理器架構的識別。 位於索引 1 的身分識別是 Microsoft intermediate language (MSIL) 的架構中性組件。 位於索引 2 的身分識別不包含架構資訊。  
  
 `Get` 通常會呼叫兩次。 第一次呼叫提供 null 值`pwzBuffer`，並設定`pcchBufferSize`適用於大小`pwzBuffer`。 第二個呼叫提供適當大小`pwzBuffer`，而且包含完成時的標準組件身分識別資料。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRProbingAssemblyEnum 介面](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
