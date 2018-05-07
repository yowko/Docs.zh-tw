---
title: CLR 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03839a2c6e52f9d2dcdd2e0941ff4fdbeb8a3a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="clr-hosting-interfaces"></a>CLR 裝載介面
本節描述 unmanaged 介面主機可用於將 common language runtime (CLR) 整合到他們的應用程式。 資訊適用於.NET Framework 2.0 版和更新版本。 這些介面來控制許多層面的執行階段，比起 1.0 和 1.1 版，請將主機啟用，並提供更緊密的整合，則 CLR 與主機的執行模式之間。  
  
 在.NET Framework 1.0 和 1.1 版中，裝載模型啟用受管理的主機載入 CLR 程序，來設定特定的設定，以及接收事件通知。 不過，在一般情況下，主應用程式和 CLR 執行獨立該處理程序。 在.NET Framework 2.0 版和更新版本中，新的抽象層可讓主機提供多目前 Win32 組件中類型所提供的資源和擴充主應用程式可以設定的功能集。  
  
## <a name="in-this-section"></a>本節內容  
 [IActionOnCLREvent 介面](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 提供方法，以執行已註冊的事件回呼。  
  
 [IApartmentCallback 介面](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 提供讓 apartment 內的回呼方法。  
  
 [IAppDomainBinding 介面](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 提供方法來設定執行階段組態。  
  
 [ICatalogServices 介面](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 提供方法來分類的服務。 （此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。  
  
 [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 提供方法，支援在主機與 CLR 有關組件之間的通訊。  
  
 [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 管理 clr，而不是由主應用程式載入的組件清單。  
  
 [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 提供方法讓主應用程式存取，並設定 CLR 的各個層面。  
  
 [ICLRDebugManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 提供方法，讓主應用程式能夠與識別項和好記的名稱產生關聯的一組工作。  
  
 [ICLRErrorReportingManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 提供方法，讓主應用程式設定錯誤報告的自訂堆積傾印。  
  
 [ICLRGCManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 提供方法，讓主應用程式能夠與 CLR 的記憶體回收系統互動。  
  
 [ICLRHostBindingPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 提供方法讓主應用程式評估和溝通變更組件的原則資訊。  
  
 [ICLRHostProtectionManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 可讓主應用程式封鎖特定的 managed 的類別、 方法、 屬性和欄位，無法在部分信任程式碼中執行。  
  
 [ICLRIoCompletionManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 實作回呼方法，可讓主應用程式通知指定的 I/O 要求之狀態的 CLR。  
  
 [ICLRMemoryNotificationCallback 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 可讓主機使用的方法類似的 Win32 報表記憶體壓力狀況`CreateMemoryResourceNotification`函式。  
  
 [ICLROnEventManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 提供方法，讓主應用程式註冊及取消註冊回呼的 CLR 事件。  
  
 [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 提供方法，讓主應用程式指定原則發生失敗和逾時所要採取的動作。  
  
 [ICLRProbingAssemblyEnum 介面](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 提供方法，讓主應用程式，以取得組件的探查識別使用的組件是 CLR 內部，不需要建立或了解該身分識別的身分識別資訊。  
  
 [ICLRReferenceAssemblyEnum 介面](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 提供方法，讓主應用程式管理的檔案或使用組件識別資料，而不需要建立，或了解這些識別的 CLR，內部資料流所參考的組件集。  
  
 [ICLRRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 提供功能類似於[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)，設定主控制項介面的其他方法。  
  
 [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 提供方法來取得要求的工作的相關資訊，並在同步處理實作偵測死結的主機。  
  
 [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 提供方法，讓主應用程式提出要求的 clr，或提供相關聯的工作有關 clr 的通知。  
  
 [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 提供方法，讓主應用程式明確要求 CLR 建立新的工作、 取得目前執行的工作，以及設定地理語言和文化特性的工作。  
  
 [ICLRValidator 介面](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 提供方法來驗證的可攜式執行檔 (PE) 影像，以及回報驗證錯誤。  
  
 [ICorConfiguration 介面](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 提供方法來設定 CLR。  
  
 [ICorThreadpool 介面](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 提供方法來存取在執行緒集區。  
  
 [IDebuggerInfo 介面](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 提供方法來取得有關偵錯服務的狀態資訊。  
  
 [IDebuggerThreadControl 介面](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 提供方法來通知主機有關封鎖及解除封鎖的執行緒，偵錯服務。  
  
 [IGCHost 介面](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。  
  
 [IGCHost2 介面](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 提供[SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法可讓主應用程式設定記憶體回收集合區段的大小和記憶體回收系統的層代零的最大值大於`DWORD`。  
  
 [IGCHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 提供方法，讓記憶體回收行程，以要求主機若要變更虛擬記憶體的限制。  
  
 [IGCThreadControl 介面](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 提供方法來參與，否則記憶體回收會封鎖執行緒的排程。  
  
 [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 提供方法，讓主應用程式指定的 clr 或主應用程式應該載入的組件集合。  
  
 [IHostAssemblyStore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 提供方法，讓主應用程式載入組件和模組與 CLR 無關。  
  
 [IHostAutoEvent 介面](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 提供主機所實作的自動重設事件的表示法。  
  
 [IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 提供設定載入的組件，以及判斷哪些裝載介面主應用程式支援的方法。  
  
 [IHostCrst 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 可做為主機的關鍵區段的執行緒的表示法。  
  
 [IHostGCManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 提供方法，以通知主機在實作 clr 記憶體回收機制中的事件。  
  
 [IHostIoCompletionManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 提供讓 CLR 與 I/O 完成通訊埠提供主機互動的方法。  
  
 [IHostMalloc 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 提供從透過主機堆積要求更細緻的配置 CLR 的方法。  
  
 [IHostManualEvent 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 提供的手動重設事件表示主機的實作。  
  
 [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 提供 CLR 的虛擬記憶體透過建立要求的主機，而不是使用標準 Win32 虛擬記憶體函式的方法。  
  
 [IHostPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 提供方法，以通知主機在 CLR 中的案例所執行的動作會中止，逾時或失敗。  
  
 [IHostSecurityContext 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 啟用 CLR 的維護主機實作的安全性內容資訊。  
  
 [IHostSecurityManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 提供方法，以啟用存取權，以及控制目前執行中執行緒的安全性內容。  
  
 [IHostSemaphore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 提供由主機實作的號誌的表示法。  
  
 [IHostSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 提供 CLR 呼叫主應用程式，而不是使用 Win32 同步處理函式來建立同步處理原始物件的方法。  
  
 [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 提供讓 CLR 與主應用程式管理工作進行通訊的方法。  
  
 [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 提供讓 CLR 工作透過主應用程式，而不是使用標準的作業系統執行緒或 fiber 函式所使用的方法。  
  
 [IHostThreadPoolManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 提供方法來設定執行緒集區和工作項目至執行緒集區佇列的 CLR。  
  
 [IManagedObject 介面](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 提供方法來控制受管理的物件。  
  
 「 IObjectHandle"  
 提供方法，以解除包裝的傳值方式封送處理物件，從間接取值。  
  
 [ITypeName 介面](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 提供方法來取得型別名稱資訊。 （此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。  
  
 [ITypeNameBuilder 介面](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 提供方法來建置型別名稱。 （此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。  
  
 [ITypeNameFactory 介面](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 提供方法來解構型別名稱。 （此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。  
  
 「 IValidator"  
 提供方法來驗證的可攜式執行檔 (PE) 影像，以及回報驗證錯誤。  
  
## <a name="related-sections"></a>相關章節  
 [已被取代的 CLR 裝載介面和 Coclass](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 包含的主題將描述裝載.NET Framework 1.0 和 1.1 版中提供的介面。  
  
 [.NET Framework 4 和 4.5 中新增的 CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 包含描述裝載介面中提供的主題[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。
