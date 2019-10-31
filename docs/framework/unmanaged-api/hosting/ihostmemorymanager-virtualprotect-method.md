---
title: IHostMemoryManager::VirtualProtect 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualProtect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type:
- apiref
ms.openlocfilehash: d39ad45e143026f40ffcf1339e923837f9e812c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195852"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a>IHostMemoryManager::VirtualProtect 方法
作為對應 Win32 函式的邏輯包裝函式。 的 Win32 執行 `VirtualProtect` 會在呼叫進程的虛擬位址空間中，變更已認可頁面區域的保護。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a>參數  
 `lpAddress`  
 在要變更其保護屬性之虛擬記憶體基底位址的指標。  
  
 `dwSize`  
 在要變更之記憶體頁面區域的大小（以位元組為單位）。  
  
 `flNewProtect`  
 在要套用的記憶體保護類型。  
  
 `pflOldProtect`  
 脫銷先前記憶體保護值的指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `VirtualProtect`。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 這個 `VirtualProtect` 的執行會傳回 HRESULT 值，而 Win32 執行則會傳回非零值以表示成功，而零值則表示失敗。 如需詳細資訊，請參閱 Windows 平臺檔。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
