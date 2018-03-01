---
title: "IHostIoCompletionManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cbb4b87b57d4f5e11a9dab04d20dfb73170bb4a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager 介面
提供方法讓 common language runtime (CLR) 與 I/O 完成通訊埠提供主機互動。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Bind 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|將控制代碼繫結到的 I/O 完成通訊埠。|  
|[CloseIoCompletionPort 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|關閉之前呼叫透過建立通訊埠`CreateIoCompletionPort`。|  
|[CreateIoCompletionPort 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|主應用程式建立新的 I/O 完成通訊埠的要求。|  
|[GetAvailableThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|取得目前未處理要求的 I/O 完成執行緒數目。|  
|[GetHostOverlappedSize 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|取得主應用程式想要附加至 I/O 要求的任何自訂資料的大小。|  
|[GetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|取得服務 I/O 要求的主機可以配置的執行緒數目上限。|  
|[GetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|取得服務 I/O 要求的主機提供的執行緒最小數目。|  
|[InitializeHostOverlapped 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|提供主機有機會初始化的 I/O 要求相關的任何自訂資料。|  
|[SetCLRIoCompletionManager 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|主機提供的介面指標[ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) CLR 所實作的執行個體。|  
|[SetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|來服務 I/O 要求中設定主應用程式指派的執行緒的數目上限。|  
|[SetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|將主應用程式應該配置的執行緒的最小數目設定為 I/O 完成。|  
  
## <a name="remarks"></a>備註  
 `IHostIoCompletionManager`對應至`ICLRIoCompletionManager`CLR 所實作的介面。 CLR 會呼叫的方法`IHostIoCompletionManager`來將控制代碼繫結至主應用程式提供，且主應用程式呼叫的方法的連接埠`ICLRIoCompletionManager`報告完成的 I/O 要求。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
