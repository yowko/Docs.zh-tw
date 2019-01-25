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
ms.openlocfilehash: 96c2081e5ff5b716c2645fa44a24f12beaa0f8e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585454"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager 介面
提供方法，可讓 common language runtime (CLR)，讓主應用程式，透過虛擬記憶體要求，而不是使用標準的 Win32 虛擬記憶體函式。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Common language runtime (CLR) 已取得指定的記憶體，作業系統會告知主應用程式。|  
|[CreateMAlloc 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|取得的介面指標[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)用來從主應用程式所建立的堆積要求記憶體配置的執行個體。|  
|[GetMemoryLoad 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|主應用程式所回報，請取得目前正在使用的實體記憶體數量。|  
|[NeedsVirtualAddressSpace 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|主應用程式，CLR 會嘗試使用指定的記憶體。|  
|[RegisterMemoryNotificationCallback 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|註冊通知目前的記憶體負載，在電腦上的 CLR 的主機會叫用的回呼函式的指標。|  
|[ReleasedVirtualAddressSpace 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|主應用程式，CLR 已完成使用指定的記憶體。|  
|[VirtualAlloc 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|做為對應的 Win32 函式，保留或認可呼叫處理序虛擬位址空間中的頁面區域的邏輯包裝函數。|  
|[VirtualFree 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|做為對應的 Win32 函式，可釋放、 取消認可，或釋放及取消認可頁面呼叫處理序虛擬位址空間內的某個區域的邏輯包裝函數。|  
|[VirtualProtect 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|做為對應的 Win32 函式，可變更的認可頁面呼叫處理序虛擬位址空間中的保護區域上的邏輯包裝函數。|  
|[VirtualQuery 方法](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|做為對應的 Win32 函式，它會擷取呼叫處理序虛擬位址空間中的頁面範圍的相關資訊的邏輯包裝函數。|  
  
## <a name="remarks"></a>備註  
 `IHostMemoryManager` 也提供 CLR，以取得透過在堆積上提出記憶體要求，並取得處理序中的記憶體不足壓力層級指標如主應用程式所報告的方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [IHostMalloc 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
