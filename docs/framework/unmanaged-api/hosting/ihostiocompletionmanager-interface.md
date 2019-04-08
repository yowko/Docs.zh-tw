---
title: IHostIoCompletionManager 介面
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c3bebe8eabd4d5fd5faec21e0b0efc408353bc2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197265"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager 介面
提供方法，可讓 common language runtime (CLR) 與主應用程式所提供的 I/O 完成連接埠進行互動。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Bind 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|將控制代碼繫結至 I/O 完成連接埠。|  
|[CloseIoCompletionPort 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|關閉透過先前呼叫所建立的連接埠`CreateIoCompletionPort`。|  
|[CreateIoCompletionPort 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|主應用程式建立新的 I/O 完成連接埠的要求。|  
|[GetAvailableThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|取得目前未處理要求的 I/O 完成執行緒的數目。|  
|[GetHostOverlappedSize 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|取得主應用程式想要附加至 I/O 要求的任何自訂資料的大小。|  
|[GetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|取得服務 I/O 要求的主機可以配置的執行緒數目上限。|  
|[GetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|取得服務 I/O 要求的主機提供的執行緒最小數目。|  
|[InitializeHostOverlapped 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|提供有機會初始化的 I/O 要求相關的任何自訂資料中的主應用程式。|  
|[SetCLRIoCompletionManager 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|主應用程式提供的介面指標[ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) ，CLR 所實作的執行個體。|  
|[SetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|I/O 要求提供服務設定主應用程式指派的執行緒的數目上限。|  
|[SetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|I/O 完成設定主應用程式應該配置的執行緒最小數目。|  
  
## <a name="remarks"></a>備註  
 `IHostIoCompletionManager` 對應至`ICLRIoCompletionManager`，CLR 所實作的介面。 CLR 會呼叫的方法`IHostIoCompletionManager`若要將控制代碼繫結至主應用程式提供，且主機會呼叫方法的連接埠`ICLRIoCompletionManager`報告的 I/O 要求完成。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
