---
title: IHostMemoryManager::VirtualQuery 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16d146766786f129d6da38bde1126ce8afe5e70f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963686"
---
# <a name="ihostmemorymanagervirtualquery-method"></a>IHostMemoryManager::VirtualQuery 方法
作為對應 Win32 函式的邏輯包裝函式。 的 Win32 執行`VirtualQuery`會在呼叫進程的虛擬位址空間中, 抓取某個頁面範圍的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a>參數  
 `lpAddress`  
 在要查詢之虛擬記憶體中的位址指標。  
  
 `lpBuffer`  
 脫銷結構的指標, 其中包含指定之記憶體區域的相關資訊。  
  
 `dwLength`  
 在`lpBuffer`指向的緩衝區大小 (以位元組為單位)。  
  
 `pResult`  
 脫銷資訊緩衝區所傳回之位元組數的指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`VirtualQuery`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `VirtualQuery`提供有關呼叫進程的虛擬位址空間中的頁面範圍的資訊。 這個執行會將`pResult`參數的值設定為資訊緩衝區中傳回的位元組數目, 並傳回 HRESULT 值。 在 Win32 `VirtualQuery`函數中, 傳回值是緩衝區大小。 如需詳細資訊, 請參閱 Windows 平臺檔。  
  
> [!IMPORTANT]
> 作業系統的執行`VirtualQuery`不會產生鎖死, 而且可以在使用者程式碼中暫停的隨機執行緒執行到完成。 在執行這個方法的主控版本時, 請特別小心。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
