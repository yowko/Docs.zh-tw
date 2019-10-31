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
ms.openlocfilehash: bc05d76795f20d28d6d2899d61dc4674ebfdca8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128654"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager 介面
提供的方法可讓 common language runtime （CLR）透過主機提出虛擬記憶體要求，而不是使用標準的 Win32 虛擬記憶體函式。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|通知主機 common language runtime （CLR）已從作業系統取得指定的記憶體。|  
|[CreateMAlloc 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|取得[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)實例的介面指標，用來向主機所建立的堆積要求記憶體配置。|  
|[GetMemoryLoad 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|取得目前正在使用的實體記憶體數量（由主機所報告）。|  
|[NeedsVirtualAddressSpace 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|通知主機 CLR 即將嘗試使用指定的記憶體。|  
|[RegisterMemoryNotificationCallback 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|註冊主機所叫用的回呼函式指標，以通知 CLR 目前電腦上的記憶體負載。|  
|[ReleasedVirtualAddressSpace 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|通知主機 CLR 已使用指定的記憶體完成。|  
|[VirtualAlloc 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|作為對應 Win32 函式的邏輯包裝函式，它會保留或認可呼叫進程之虛擬位址空間中的頁面區域。|  
|[VirtualFree 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|做為對應的 Win32 函式的邏輯包裝函式，它會釋放、解除或釋放和解除呼叫進程之虛擬位址空間內的頁面區域。|  
|[VirtualProtect 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|做為對應的 Win32 函式的邏輯包裝函式，它會在呼叫進程的虛擬位址空間中變更已認可頁面區域的保護。|  
|[VirtualQuery 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|做為對應的 Win32 函式的邏輯包裝函式，它會在呼叫進程的虛擬位址空間中，抓取某個頁面範圍的相關資訊。|  
  
## <a name="remarks"></a>備註  
 `IHostMemoryManager` 也會提供方法，讓 CLR 取得要在堆積上進行記憶體要求的指標，以及取得進程中的記憶體壓力層級（由主機所報告）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IHostMalloc 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
