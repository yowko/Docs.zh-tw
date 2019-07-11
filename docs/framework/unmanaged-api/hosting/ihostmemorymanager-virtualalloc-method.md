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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a0764cb212a95412a4dcf9455b7648ee863951e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767672"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc 方法
可做為對應的 Win32 函式的邏輯包裝函式。 Win32 實作`VirtualAlloc`保留或認可呼叫處理序虛擬位址空間中的頁面區域。  
  
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
 [in]要配置的區域的起始位址指標。  
  
 `dwSize`  
 [in]以位元組為單位的區域大小。  
  
 `flAllocationType`  
 [in]記憶體配置的類型。  
  
 `flProtect`  
 [in]記憶體保護區要配置的頁數。  
  
 `dwCriticalLevel`  
 [in][EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)值，指出發生配置失敗的影響。  
  
 `ppMem`  
 [out]配置的記憶體或如果無法滿足要求為 null 的起始位址指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可完成配置要求|  
  
## <a name="remarks"></a>備註  
 在您的程序的位址空間保留區藉由呼叫`VirtualAlloc`。 `pAddress`參數包含您想要的記憶體區塊的開始位址。 此參數通常設為 null。 作業系統會保留您的程序可使用可用的位址範圍的記錄。 A`pAddress`是 null 的值會指示系統保留的區域，只要其認為適合。 或者，您可以提供特定的起始位址的記憶體區塊。 在這兩種情況下，輸出參數`ppMem`指標傳回給所配置的記憶體。 函式本身傳回的 HRESULT 值。  
  
 Win32`VirtualAlloc`函式沒有`ppMem`參數，並改為傳回配置的記憶體指標。 如需詳細資訊，請參閱 Windows 平台的文件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
