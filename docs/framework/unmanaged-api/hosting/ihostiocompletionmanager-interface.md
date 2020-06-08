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
ms.openlocfilehash: 095872f8d4bd4f7d3351b8b3e3f8f8445b615cd8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501531"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager 介面
提供的方法可讓 common language runtime （CLR）與主機所提供的 i/o 完成通訊埠互動。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Bind 方法](ihostiocompletionmanager-bind-method.md)|將控制碼系結到 i/o 完成通訊埠。|  
|[CloseIoCompletionPort 方法](ihostiocompletionmanager-closeiocompletionport-method.md)|關閉透過先前的呼叫所建立的埠 `CreateIoCompletionPort` 。|  
|[CreateIoCompletionPort 方法](ihostiocompletionmanager-createiocompletionport-method.md)|要求主機建立新的 i/o 完成埠。|  
|[GetAvailableThreads 方法](ihostiocompletionmanager-getavailablethreads-method.md)|取得目前未處理要求的 i/o 完成執行緒數目。|  
|[GetHostOverlappedSize 方法](ihostiocompletionmanager-gethostoverlappedsize-method.md)|取得主機打算附加到 i/o 要求的任何自訂資料大小。|  
|[GetMaxThreads 方法](ihostiocompletionmanager-getmaxthreads-method.md)|取得主機可以為服務 i/o 要求所分配的執行緒數目上限。|  
|[GetMinThreads 方法](ihostiocompletionmanager-getminthreads-method.md)|取得主機提供給服務 i/o 要求的執行緒數目下限。|  
|[InitializeHostOverlapped 方法](ihostiocompletionmanager-initializehostoverlapped-method.md)|提供主機初始化 i/o 要求之任何自訂資料的機會。|  
|[SetCLRIoCompletionManager 方法](ihostiocompletionmanager-setclriocompletionmanager-method.md)|提供具有 CLR 所實[ICLRIoCompletionManager](iclriocompletionmanager-interface.md)實例之介面指標的主機。|  
|[SetMaxThreads 方法](ihostiocompletionmanager-setmaxthreads-method.md)|設定主機 allots 至服務 i/o 要求的執行緒數目上限。|  
|[SetMinThreads 方法](ihostiocompletionmanager-setminthreads-method.md)|設定主機應該為 i/o 完成所配置的執行緒數目下限。|  
  
## <a name="remarks"></a>備註  
 `IHostIoCompletionManager`對應至 `ICLRIoCompletionManager` CLR 所執行的介面。 CLR 會呼叫的方法， `IHostIoCompletionManager` 將控制碼系結至主機提供的埠，而主機會呼叫的方法 `ICLRIoCompletionManager` 來報告 i/o 要求的完成。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
