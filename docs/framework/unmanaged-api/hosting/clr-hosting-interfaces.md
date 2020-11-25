---
title: CLR 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: 77f2ba64d9bdbe9793d56e88dae46fd506119ab8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719043"
---
# <a name="clr-hosting-interfaces"></a>CLR 裝載介面

本節說明非受控主機可用來將 common language runtime (CLR) 整合至其應用程式的介面。 .NET Framework 版本2.0 和更新版本的相關資訊。 這些介面可讓主控制項控制執行時間的許多層面，而不是1.0 和1.1 版本中可能的版本，並在 CLR 與主機的執行模型之間提供更緊密的整合。  
  
 在 .NET Framework 1.0 和1.1 版中，裝載模型已啟用非受控主機，以將 CLR 載入至進程、設定特定設定，以及接收事件通知。 不過，一般而言，主機和 CLR 會在該進程中獨立執行。 在 .NET Framework 2.0 版和更新版本中，新的抽象層可讓主機提供 Win32 元件中類型目前提供的許多資源，並擴充主機可以設定的一組功能。  
  
## <a name="in-this-section"></a>本節內容  

 [IActionOnCLREvent 介面](iactiononclrevent-interface.md)  
 提供方法，此方法會針對已註冊的事件執行回呼。  
  
 [IApartmentCallback 介面](iapartmentcallback-interface.md)  
 提供在一個單元內進行回呼的方法。  
  
 [IAppDomainBinding 介面](iappdomainbinding-interface.md)  
 提供用來設定執行時間設定的方法。  
  
 [ICatalogServices 介面](icatalogservices-interface.md)  
 提供編目服務的方法。  (此介面支援 .NET Framework 基礎結構，而且不適合直接從程式碼使用。 )   
  
 [ICLRAssemblyIdentityManager 介面](iclrassemblyidentitymanager-interface.md)  
 提供的方法可支援主機和 CLR 與元件之間的通訊。  
  
 [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)  
 管理由 CLR 載入的元件清單，而不是由主機載入的元件清單。  
  
 [ICLRControl 介面](iclrcontrol-interface.md)  
 提供方法讓主機取得和設定 CLR 的各個層面。  
  
 [ICLRDebugManager 介面](iclrdebugmanager-interface.md)  
 提供可讓主控制項將一組工作與識別碼和易記名稱產生關聯的方法。  
  
 [ICLRErrorReportingManager 介面](iclrerrorreportingmanager-interface.md)  
 提供可讓主機針對錯誤報表設定自訂堆積傾印的方法。  
  
 [ICLRGCManager 介面](iclrgcmanager-interface.md)  
 提供可讓主控制項與 CLR 的垃圾收集系統互動的方法。  
  
 [ICLRHostBindingPolicyManager 介面](iclrhostbindingpolicymanager-interface.md)  
 提供方法，讓主機評估及傳達元件的原則資訊變更。  
  
 [ICLRHostProtectionManager 介面](iclrhostprotectionmanager-interface.md)  
 讓主機封鎖特定的 managed 類別、方法、屬性和欄位，使其無法在部分信任的程式碼中執行。  
  
 [ICLRIoCompletionManager 介面](iclriocompletionmanager-interface.md)  
 執行回呼方法，這個方法可讓主機通知 CLR 所指定 i/o 要求的狀態。  
  
 [ICLRMemoryNotificationCallback 介面](iclrmemorynotificationcallback-interface.md)  
 使用與 Win32 函數類似的方法，讓主機能夠報告記憶體壓力條件 `CreateMemoryResourceNotification` 。  
  
 [ICLROnEventManager 介面](iclroneventmanager-interface.md)  
 提供可讓主機針對 CLR 事件註冊和取消註冊回呼的方法。  
  
 [ICLRPolicyManager 介面](iclrpolicymanager-interface.md)  
 提供的方法，可讓主機指定發生失敗和超時時所要採取的原則動作。  
  
 [ICLRProbingAssemblyEnum 介面](iclrprobingassemblyenum-interface.md)  
 提供的方法可讓主機使用 CLR 內部的元件身分識別資訊來取得元件的探查識別，而不需要建立或瞭解該身分識別。  
  
 [ICLRReferenceAssemblyEnum 介面](iclrreferenceassemblyenum-interface.md)  
 提供的方法可讓主機使用 CLR 內部的元件身分識別資料，來操作檔案或資料流程所參考的元件集合，而不需要建立或瞭解這些身分識別。  
  
 [ICLRRuntimeHost 介面](iclrruntimehost-interface.md)  
 提供與 [ICorRuntimeHost](icorruntimehost-interface.md)類似的功能，並提供可設定主控制項介面的額外方法。  
  
 [ICLRSyncManager 介面](iclrsyncmanager-interface.md)  
 提供方法，讓主機取得所要求之工作的相關資訊，並偵測其同步處理執行中的鎖死。  
  
 [ICLRTask 介面](iclrtask-interface.md)  
 提供可讓主機提出 CLR 要求的方法，或提供有關相關聯工作之 CLR 的通知。  
  
 [ICLRTaskManager 介面](iclrtaskmanager-interface.md)  
 提供的方法可讓主機明確要求 CLR 建立新的工作、取得目前正在執行的工作，以及設定工作的地理語言和文化特性。  
  
 [ICLRValidator 介面](iclrvalidator-interface.md)  
 提供驗證可攜式可執行檔 (PE) 映射和報告驗證錯誤的方法。  
  
 [ICorConfiguration 介面](icorconfiguration-interface.md)  
 提供設定 CLR 的方法。  
  
 [ICorThreadpool 介面](icorthreadpool-interface.md)  
 提供存取執行緒集區的方法。  
  
 [IDebuggerInfo 介面](idebuggerinfo-interface.md)  
 提供方法，以取得有關偵錯工具狀態的資訊。  
  
 [IDebuggerThreadControl 介面](idebuggerthreadcontrol-interface.md)  
 提供方法，通知主機有關偵錯工具的執行緒封鎖和解除封鎖。  
  
 [IGCHost 介面](igchost-interface.md)  
 提供方法來取得垃圾收集系統的相關資訊，以及控制垃圾收集的某些層面。  
  
 [IGCHost2 介面](igchost2-interface.md)  
 提供 [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) 方法，可讓主控制項將垃圾收集區段的大小以及垃圾收集系統層代零的大小上限設定為大於 `DWORD` 的值。  
  
 [IGCHostControl 介面](igchostcontrol-interface.md)  
 提供一種方法，可讓垃圾收集行程要求主控制項變更虛擬記憶體的限制。  
  
 [IGCThreadControl 介面](igcthreadcontrol-interface.md)  
 提供方法來參與執行緒的排程，而這些執行緒會被封鎖以進行垃圾收集。  
  
 [IHostAssemblyManager 介面](ihostassemblymanager-interface.md)  
 提供的方法，可讓主機指定要由 CLR 或主機載入的元件集。  
  
 [IHostAssemblyStore 介面](ihostassemblystore-interface.md)  
 提供可讓主機獨立于 CLR 之外載入元件和模組的方法。  
  
 [IHostAutoEvent 介面](ihostautoevent-interface.md)  
 提供主機所執行之自動重設事件的標記法。  
  
 [IHostControl 介面](ihostcontrol-interface.md)  
 提供方法來設定元件的載入，以及判斷主機所支援的裝載介面。  
  
 [IHostCrst 介面](ihostcrst-interface.md)  
 作為執行緒的重要區段的主機標記法。  
  
 [IHostGCManager 介面](ihostgcmanager-interface.md)  
 提供方法，以在 CLR 所執行的垃圾收集機制中通知主機事件。  
  
 [IHostIoCompletionManager 介面](ihostiocompletionmanager-interface.md)  
 提供可讓 CLR 與主機所提供的 i/o 完成通訊埠互動的方法。  
  
 [IHostMalloc 介面](ihostmalloc-interface.md)  
 提供方法，讓 CLR 透過主控制項向堆積要求更精細的配置。  
  
 [IHostManualEvent 介面](ihostmanualevent-interface.md)  
 提供主機手動重設事件標記法的實作為。  
  
 [IHostMemoryManager 介面](ihostmemorymanager-interface.md)  
 提供方法讓 CLR 透過主機提出虛擬記憶體要求，而不是使用標準 Win32 虛擬記憶體函式。  
  
 [IHostPolicyManager 介面](ihostpolicymanager-interface.md)  
 提供方法，以通知主機 CLR 在中止、超時或失敗時所執行的動作。  
  
 [IHostSecurityContext 介面](ihostsecuritycontext-interface.md)  
 讓 CLR 維護主機所執行的安全性內容資訊。  
  
 [IHostSecurityManager 介面](ihostsecuritymanager-interface.md)  
 提供方法，可讓您存取和控制目前執行中線程的安全性內容。  
  
 [IHostSemaphore 介面](ihostsemaphore-interface.md)  
 提供主機所執行之信號的標記法。  
  
 [IHostSyncManager 介面](ihostsyncmanager-interface.md)  
 提供方法，讓 CLR 藉由呼叫主機來建立同步處理原始物件，而不是使用 Win32 同步處理函數。  
  
 [IHostTask 介面](ihosttask-interface.md)  
 提供可讓 CLR 與主機通訊以管理工作的方法。  
  
 [IHostTaskManager 介面](ihosttaskmanager-interface.md)  
 提供可讓 CLR 透過主機處理工作的方法，而不是使用標準作業系統執行緒或光纖函數。  
  
 [IHostThreadPoolManager 介面](ihostthreadpoolmanager-interface.md)  
 提供方法讓 CLR 設定執行緒集區，並將工作專案加入執行緒集區。  
  
 [IManagedObject 介面](imanagedobject-interface.md)  
 提供控制 managed 物件的方法。  
  
 IObjectHandle  
 提供方法來解除包裝從間接取值的封送處理物件。  
  
 [ITypeName 介面](itypename-interface.md)  
 提供取得型別名稱資訊的方法。  (此介面支援 .NET Framework 基礎結構，而且不適合直接從程式碼使用。 )   
  
 [ITypeNameBuilder 介面](itypenamebuilder-interface.md)  
 提供建立型別名稱的方法。  (此介面支援 .NET Framework 基礎結構，而且不適合直接從程式碼使用。 )   
  
 [ITypeNameFactory 介面](itypenamefactory-interface.md)  
 提供解構型別名稱的方法。  (此介面支援 .NET Framework 基礎結構，而且不適合直接從程式碼使用。 )   
  
 IValidator  
 提供驗證可攜式可執行檔 (PE) 映射和報告驗證錯誤的方法。  
  
## <a name="related-sections"></a>相關章節  

 [已被取代的 CLR 裝載介面和 Coclass](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 包含描述 .NET Framework 版本1.0 和1.1 中所提供之裝載介面的主題。  
  
 [.NET Framework 4 和 4.5 中新增的 CLR 裝載介面](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 包含描述 .NET Framework 4 中所提供之裝載介面的主題。
