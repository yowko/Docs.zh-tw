---
title: ICLRReferenceAssemblyEnum::Get 方法
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
ms.openlocfilehash: 3968adf418fcea847ee2be5a412385d041a53544
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728898"
---
# <a name="iclrreferenceassemblyenumget-method"></a>ICLRReferenceAssemblyEnum::Get 方法

取得提供的索引處的元件識別。  
  
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
 在要傳回的元件識別之以零為基底的索引。  
  
 `pwzBuffer`  
 擴展包含元件身分識別資料的緩衝區。  
  
 `pcchBufferSize`  
 [in，out]緩衝區的大小 `pwzBuffer` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`Get` 傳回成功。|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` 太小了。|  
|ERROR_NO_MORE_ITEMS|列舉中不包含任何專案。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 `Get` 通常會呼叫兩次。 第一個呼叫會提供的 null 值 `pwzBuffer` ，並將設定 `pcchBufferSize` 為適合的大小 `pwzBuffer` 。 第二個呼叫會提供適當大小 `pwzBuffer` ，並在完成時包含標準的元件身分識別資料。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [ICLRReferenceAssemblyEnum 介面](iclrreferenceassemblyenum-interface.md)
