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
ms.openlocfilehash: 028ca0b9cb917d3e6cc0242cbc8c3f4a5a19ab39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760099"
---
# <a name="ihostmemorymanagervirtualquery-method"></a>IHostMemoryManager::VirtualQuery 方法
可做為對應的 Win32 函式的邏輯包裝函式。 Win32 實作`VirtualQuery`擷取呼叫處理序虛擬位址空間中的頁面範圍的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a>參數  
 `lpAddress`  
 [in]要查詢的虛擬記憶體中的位址指標。  
  
 `lpBuffer`  
 [out]包含指定的記憶體區域的相關資訊的結構指標。  
  
 `dwLength`  
 [in]大小，以位元組為單位的緩衝區，`lpBuffer`指向。  
  
 `pResult`  
 [out]傳回的資訊緩衝區的位元組數目指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`VirtualQuery` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `VirtualQuery` 提供呼叫的處理序虛擬位址空間中的頁面範圍的相關資訊。 此實作中設定的值`pResult`的位元組數目的參數傳回資訊的緩衝區，並傳回 HRESULT 值。 在 Win32 中`VirtualQuery`函式，傳回的值是緩衝區大小。 如需詳細資訊，請參閱 Windows 平台的文件。  
  
> [!IMPORTANT]
>  作業系統的實作`VirtualQuery`不會產生死結，並使用隨機使用者程式碼中暫止的執行緒可以執行到完成為止。 實作這個方法的裝載的版本時，請使用很棒的注意。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
