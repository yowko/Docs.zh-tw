---
title: IHostMemoryManager::VirtualFree 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
ms.openlocfilehash: b53c0bb38922ae8de048c131807eb32f97423d6c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128583"
---
# <a name="ihostmemorymanagervirtualfree-method"></a>IHostMemoryManager::VirtualFree 方法
作為對應 Win32 函式的邏輯包裝函式。 的 Win32 執行 `VirtualFree` 在呼叫進程的虛擬位址空間內，釋放、解除或釋放和解除頁面的區域。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a>參數  
 `lpAddress`  
 在要釋放之虛擬記憶體頁面的基底位址指標。  
  
 `dwSize`  
 在要釋放之區域的大小（以位元組為單位）。  
  
 `dwFreeType`  
 在釋放作業的類型。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `VirtualFree`。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_INVALIDOPERATION|嘗試釋放未透過主機所配置的記憶體。|  
  
## <a name="remarks"></a>備註  
 `VirtualFree` 透過先前對[IHostMemoryManager：： VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)函數的呼叫，釋放與 `lpAddress` 參數相關聯的虛擬記憶體頁面。 嘗試釋放未透過主機配置的記憶體時，應該會傳回 HOST_E_INVALIDOPERATION。  
  
 此語義與 `VirtualFree`的 Win32 執行方式相同。 如需詳細資訊，請參閱 Windows 平臺檔。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
