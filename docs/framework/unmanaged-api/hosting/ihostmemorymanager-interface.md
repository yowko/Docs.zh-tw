---
title: IHostMemoryManager 介面
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3edae4cb112f46643734c5f1612d9df36ad47e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441320"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager 介面
提供方法讓 common language runtime (CLR) 進行透過主機的虛擬記憶體要求，而不是使用標準 Win32 虛擬記憶體函式。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|通知主機 common language runtime (CLR) 已取得作業系統中指定的記憶體。|  
|[CreateMAlloc 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|取得的介面指標[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)用來要求從主應用程式所建立的堆積記憶體配置的執行個體。|  
|[GetMemoryLoad 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|主應用程式報告，取得目前正在使用的實體記憶體數量。|  
|[NeedsVirtualAddressSpace 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|通知主機在 CLR 會嘗試使用指定的記憶體。|  
|[RegisterMemoryNotificationCallback 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|註冊通知的電腦上目前的記憶體負載 CLR 的主機會叫用的回呼函式的指標。|  
|[ReleasedVirtualAddressSpace 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|通知主機在 CLR 已經完成使用指定的記憶體。|  
|[VirtualAlloc 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|可做為對應的 Win32 函式，保留或認可呼叫的處理序的虛擬位址空間中的頁面區域的邏輯包裝函式。|  
|[VirtualFree 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|可做為對應的 Win32 函式，以釋放、 取消的認可，或釋放和取消認可呼叫的處理序的虛擬位址空間中的頁面區域的邏輯包裝函式。|  
|[VirtualProtect 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|可做為對應的 Win32 函式，可變更的認可頁面呼叫處理序的虛擬位址空間中的保護區域上的邏輯包裝函式。|  
|[VirtualQuery 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|可做為對應的 Win32 函式，會擷取呼叫處理序的虛擬位址空間中的頁面範圍的相關資訊的邏輯包裝函式。|  
  
## <a name="remarks"></a>備註  
 `IHostMemoryManager` 也提供 CLR，以取得的指標，請在堆積上之記憶體要求，並取得處理序中的記憶體不足壓力層級透過主應用程式所報告的方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IHostMalloc 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
