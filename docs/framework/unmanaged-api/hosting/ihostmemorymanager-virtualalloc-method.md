---
title: "IHostMemoryManager::VirtualAlloc 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 761958c44ad374d522a52826929e320e65957ffa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc 方法
可做為對應的 Win32 函式的邏輯包裝函式。 Win32 實作`VirtualAlloc`保留或認可呼叫的處理序的虛擬位址空間中的頁面區域。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAddress`  
 [in]要配置的區域的起始位址指標。  
  
 `dwSize`  
 [in]以位元組為單位，區域的大小。  
  
 `flAllocationType`  
 [in]記憶體配置的類型。  
  
 `flProtect`  
 [in]記憶體保護區域的配置的頁數。  
  
 `dwCriticalLevel`  
 [in][EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)值，指出配置失敗的影響。  
  
 `ppMem`  
 [out]配置的記憶體或如果無法滿足要求為 null 的起始位址指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 方法會傳回 E_FAIL CLR 已不再可用的處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可完成配置要求。|  
  
## <a name="remarks"></a>備註  
 在您的處理序的位址空間保留區藉由呼叫`VirtualAlloc`。 `pAddress`參數包含您想要的記憶體區塊的開始位址。 此參數通常設定為 null。 作業系統會保留您的程序可使用可用的位址範圍的記錄。 A `pAddress` null 值會指示保留區域，只要得以透過適當的系統。 或者，您可以提供特定的起始位址的記憶體區塊。 在這兩種情況下，輸出參數`ppMem`傳回的指標至配置的記憶體。 函式本身傳回的 HRESULT 值。  
  
 Win32`VirtualAlloc`函式沒有`ppMem`參數，並改為傳回配置的記憶體指標。 如需詳細資訊，請參閱 Windows 平台的文件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
