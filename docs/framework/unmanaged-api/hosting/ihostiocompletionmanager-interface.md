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
ms.openlocfilehash: 51d79c398c94ec355528140325da2c25422cbad9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133853"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager 介面
提供的方法可讓 common language runtime （CLR）與主機所提供的 i/o 完成通訊埠互動。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Bind 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|將控制碼系結到 i/o 完成通訊埠。|  
|[CloseIoCompletionPort 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|關閉透過先前的 `CreateIoCompletionPort`呼叫所建立的埠。|  
|[CreateIoCompletionPort 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|要求主機建立新的 i/o 完成埠。|  
|[GetAvailableThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|取得目前未處理要求的 i/o 完成執行緒數目。|  
|[GetHostOverlappedSize 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|取得主機打算附加到 i/o 要求的任何自訂資料大小。|  
|[GetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|取得主機可以為服務 i/o 要求所分配的執行緒數目上限。|  
|[GetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|取得主機提供給服務 i/o 要求的執行緒數目下限。|  
|[InitializeHostOverlapped 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|提供主機初始化 i/o 要求之任何自訂資料的機會。|  
|[SetCLRIoCompletionManager 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|提供具有 CLR 所實[ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)實例之介面指標的主機。|  
|[SetMaxThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|設定主機 allots 至服務 i/o 要求的執行緒數目上限。|  
|[SetMinThreads 方法](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|設定主機應該為 i/o 完成所配置的執行緒數目下限。|  
  
## <a name="remarks"></a>備註  
 `IHostIoCompletionManager` 對應至 CLR 所實的 `ICLRIoCompletionManager` 介面。 CLR 會呼叫 `IHostIoCompletionManager` 的方法，將控制碼系結至主機提供的埠，而主機則會呼叫 `ICLRIoCompletionManager` 的方法，以報告 i/o 要求的完成。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
