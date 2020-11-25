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
ms.openlocfilehash: 75ad8670008242008aa344835143ff9b2add0a6c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719589"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager 介面

提供方法，讓 common language runtime (CLR) 與主機所提供的 i/o 完成埠互動。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Bind 方法](ihostiocompletionmanager-bind-method.md)|將控制碼系結至 i/o 完成通訊埠。|  
|[CloseIoCompletionPort 方法](ihostiocompletionmanager-closeiocompletionport-method.md)|關閉透過先前的呼叫所建立的埠 `CreateIoCompletionPort` 。|  
|[CreateIoCompletionPort 方法](ihostiocompletionmanager-createiocompletionport-method.md)|要求主機建立新的 i/o 完成通訊埠。|  
|[GetAvailableThreads 方法](ihostiocompletionmanager-getavailablethreads-method.md)|取得目前未處理要求的 i/o 完成執行緒數目。|  
|[GetHostOverlappedSize 方法](ihostiocompletionmanager-gethostoverlappedsize-method.md)|取得主機打算附加至 i/o 要求的任何自訂資料大小。|  
|[GetMaxThreads 方法](ihostiocompletionmanager-getmaxthreads-method.md)|取得主機可為服務 i/o 要求所分配的最大執行緒數目。|  
|[GetMinThreads 方法](ihostiocompletionmanager-getminthreads-method.md)|取得主機提供給服務 i/o 要求的執行緒數目下限。|  
|[InitializeHostOverlapped 方法](ihostiocompletionmanager-initializehostoverlapped-method.md)|提供主機有機會初始化任何有關 i/o 要求的自訂資料。|  
|[SetCLRIoCompletionManager 方法](ihostiocompletionmanager-setclriocompletionmanager-method.md)|為主機提供由 CLR 所執行之 [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) 實例的介面指標。|  
|[SetMaxThreads 方法](ihostiocompletionmanager-setmaxthreads-method.md)|設定主機 allots 至服務 i/o 要求的最大執行緒數目。|  
|[SetMinThreads 方法](ihostiocompletionmanager-setminthreads-method.md)|設定主機應該為 i/o 完成配置的執行緒數目下限。|  
  
## <a name="remarks"></a>備註  

 `IHostIoCompletionManager` 對應至 `ICLRIoCompletionManager` CLR 所執行的介面。 CLR 會呼叫的方法 `IHostIoCompletionManager` ，將控制碼系結至主機提供的埠，而主機會呼叫的方法， `ICLRIoCompletionManager` 以報告 i/o 要求的完成。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
