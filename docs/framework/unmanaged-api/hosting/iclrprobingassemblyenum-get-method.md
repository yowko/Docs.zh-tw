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
ms.openlocfilehash: 2ff1f9428a92d091a51a4cca12d69d98da0ecba2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120529"
---
# <a name="iclrprobingassemblyenumget-method"></a>ICLRProbingAssemblyEnum::Get 方法
取得指定索引處的元件識別。  
  
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
 在要傳回之元件身分識別的以零為起始的索引。  
  
 `pwzBuffer`  
 脫銷包含元件識別資料的緩衝區。  
  
 `pcchBufferSize`  
 [in、out]`pwzBuffer` 緩衝區的大小。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `Get`。|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` 太小。|  
|ERROR_NO_MORE_ITEMS|列舉不包含其他專案。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。 對任何裝載方法的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 位於索引0的識別是處理器架構特有的身分識別。 位於索引1的識別是 Microsoft 中繼語言（MSIL）的架構中立元件。 位於索引2的識別不包含架構資訊。  
  
 `Get` 通常會被呼叫兩次。 第一個呼叫會為 `pwzBuffer`提供 null 值，並將 `pcchBufferSize` 設定為適用于 `pwzBuffer`的大小。 第二個呼叫會提供適當大小的 `pwzBuffer`，並在完成時包含標準的元件識別資料。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRProbingAssemblyEnum 介面](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
