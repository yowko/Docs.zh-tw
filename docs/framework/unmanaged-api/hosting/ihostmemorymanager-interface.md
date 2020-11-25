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
ms.openlocfilehash: 0f71e4c45e43c2027b12998532f2b04401a51951
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731328"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager 介面

提供可讓 common language runtime (CLR) 透過主機提出虛擬記憶體要求的方法，而不是使用標準的 Win32 虛擬記憶體函式。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace 方法](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|通知主機 common language runtime (CLR) 已從作業系統取得指定的記憶體。|  
|[CreateMAlloc 方法](ihostmemorymanager-createmalloc-method.md)|取得 [IHostMAlloc](ihostmalloc-interface.md) 實例的介面指標，該實例用來從主控制項建立的堆積要求記憶體配置。|  
|[GetMemoryLoad 方法](ihostmemorymanager-getmemoryload-method.md)|取得目前正在使用的實體記憶體數量，如主機所報告。|  
|[NeedsVirtualAddressSpace 方法](ihostmemorymanager-needsvirtualaddressspace-method.md)|通知主機 CLR 即將嘗試使用指定的記憶體。|  
|[RegisterMemoryNotificationCallback 方法](ihostmemorymanager-registermemorynotificationcallback-method.md)|註冊回呼函式的指標，主機會叫用該函式來通知 CLR 目前電腦上的記憶體負載。|  
|[ReleasedVirtualAddressSpace 方法](ihostmemorymanager-releasedvirtualaddressspace-method.md)|通知主機 CLR 已完成使用指定的記憶體。|  
|[VirtualAlloc 方法](ihostmemorymanager-virtualalloc-method.md)|作為對應 Win32 函數的邏輯包裝函式，它會保留或認可呼叫進程之虛擬位址空間中的頁面區域。|  
|[VirtualFree 方法](ihostmemorymanager-virtualfree-method.md)|做為對應 Win32 函數的邏輯包裝函式，它會在呼叫進程的虛擬位址空間內釋放、解除或釋放和解除頁面區域。|  
|[VirtualProtect 方法](ihostmemorymanager-virtualprotect-method.md)|作為對應 Win32 函數的邏輯包裝函式，它會在呼叫進程的虛擬位址空間中變更已認可頁面區域的保護。|  
|[VirtualQuery 方法](ihostmemorymanager-virtualquery-method.md)|做為對應 Win32 函數的邏輯包裝函式，它會在呼叫進程的虛擬位址空間中抓取頁面範圍的相關資訊。|  
  
## <a name="remarks"></a>備註  

 `IHostMemoryManager` 也提供方法，讓 CLR 取得用來在堆積上提出記憶體要求的指標，以及取得進程中的記憶體壓力層級，如主機所報告。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostMalloc 介面](ihostmalloc-interface.md)
- [裝載介面](hosting-interfaces.md)
