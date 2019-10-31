---
title: IHostMemoryManager::GetMemoryLoad 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
ms.openlocfilehash: 2210dcd9e8a8af92b7905ec680c53c1119e6a3cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136712"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a>IHostMemoryManager::GetMemoryLoad 方法
取得目前使用中的實體記憶體數量，因此無法供主機報告。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a>參數  
 `pMemoryLoad`  
 脫銷目前使用中實體記憶體總計的大約百分比指標。  
  
 `pAvailableBytes`  
 脫銷通用語言執行時間（CLR）可用位元組數的指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `GetMemoryLoad`。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `GetMemoryLoad` 包裝 Win32 `GlobalMemoryStatus` 函數。 `pMemoryLoad` 的值等同于 `GlobalMemoryStatus`所傳回 `MEMORYSTATUS` 結構中的 `dwMemoryLoad` 欄位。  
  
 執行時間會使用傳回值做為垃圾收集行程的啟發學習法。 例如，如果主機報告大部分的記憶體正在使用中，垃圾收集行程可能會選擇從多個層代收集，以增加可能會變成可用的記憶體數量。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.GC?displayProperty=nameWithType>
- [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
