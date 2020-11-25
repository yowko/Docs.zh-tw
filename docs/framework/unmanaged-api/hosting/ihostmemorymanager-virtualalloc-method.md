---
title: IHostMemoryManager::VirtualAlloc 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
ms.openlocfilehash: a2deabc5f1c7ea0f42b6d8ec3944d984854ae571
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731276"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc 方法

作為對應 Win32 函數的邏輯包裝函式。 的 Win32 執行會 `VirtualAlloc` 保留或認可呼叫進程之虛擬位址空間中的頁面區域。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>參數  

 `pAddress`  
 在要配置之區域的起始位址指標。  
  
 `dwSize`  
 在區域的大小（以位元組為單位）。  
  
 `flAllocationType`  
 在記憶體配置的類型。  
  
 `flProtect`  
 在要配置之頁面區域的記憶體保護。  
  
 `dwCriticalLevel`  
 在 [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) 值，表示配置失敗的影響。  
  
 `ppMem`  
 擴展配置的記憶體之起始位址的指標，如果無法滿足要求，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|可用的記憶體不足，無法完成配置要求|  
  
## <a name="remarks"></a>備註  

 您可以藉由呼叫，在進程的位址空間中保留一個區域 `VirtualAlloc` 。 `pAddress`參數包含您想要之記憶體區塊的起始位址。 此參數通常會設定為 null。 作業系統會保留您的進程可用的免費位址範圍記錄。 若 `pAddress` 值為 null，則會指示系統保留區域以符合的位置。 或者，您可以為記憶體區塊提供特定的起始位址。 在這兩種情況下，輸出參數 `ppMem` 會以指標的形式傳回給配置的記憶體。 函數本身會傳回 HRESULT 值。  
  
 Win32 `VirtualAlloc` 函數沒有 `ppMem` 參數，而是改為將指標傳回給配置的記憶體。 如需詳細資訊，請參閱 Windows 平臺檔。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostMemoryManager 介面](ihostmemorymanager-interface.md)
