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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789658"
---
# <a name="clr-hosting-interfaces"></a>CLR 裝載介面
本節描述 unmanaged 介面主機可用來將 common language runtime (CLR) 整合到他們的應用程式。 此資訊適用於.NET Framework 2.0 版和更新版本。 這些介面讓控制許多的更多方面，比在 1.0 和 1.1 版中的執行階段主應用程式，並提供 CLR 與主機的執行模式之間更緊密整合。  
  
 在.NET Framework 1.0 和 1.1 版中，主控模型會啟用受管理的主機將 CLR 載入處理序，來設定特定的設定，以及接收事件通知。 不過，在一般情況下，主應用程式和 CLR 獨立執行該程序中。 在.NET Framework 2.0 版和更新版本中，新的抽象層可讓主機提供許多 Win32 組件中的型別由目前提供的資源和擴充主應用程式可以設定的功能集。  
  
## <a name="in-this-section"></a>本節內容  
 [IActionOnCLREvent 介面](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 提供針對已註冊的事件執行的回呼方法。  
  
 [IApartmentCallback 介面](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 提供方法來進行回呼的 apartment 中。  
  
 [IAppDomainBinding 介面](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 提供方法來設定執行階段組態。  
  
 [ICatalogServices 介面](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 提供方法來編製目錄服務。 （此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。  
  
 [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 提供方法，支援在主機與 CLR 有關組件之間的通訊。  
  
 [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 管理組件載入 clr，而不是由主應用程式的清單。  
  
 [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 提供方法讓主應用程式取得存取權，以及設定 CLR 的各個層面。  
  
 [ICLRDebugManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 提供方法，讓主應用程式相關聯的一組工作識別碼和易記名稱。  
  
 [ICLRErrorReportingManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 提供方法，讓主應用程式設定錯誤報告的自訂堆積傾印。  
  
 [ICLRGCManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 提供方法，讓主應用程式能夠與 CLR 的記憶體回收系統互動。  
  
 [ICLRHostBindingPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 提供方法供主機用來評估，並傳達變更組件的原則資訊。  
  
 [ICLRHostProtectionManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 可讓主應用程式封鎖特定的 managed 的類別、 方法、 屬性和欄位，無法在部分信任程式碼中執行。  
  
 [ICLRIoCompletionManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 實作回呼方法，可讓主應用程式向 CLR 通知將指定的 I/O 要求的狀態。  
  
 [ICLRMemoryNotificationCallback 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 可讓主應用程式使用的 Win32 類似的方法報告記憶體壓力狀況`CreateMemoryResourceNotification`函式。  
  
 [ICLROnEventManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 提供可讓主應用程式註冊和取消註冊 CLR 事件的回呼方法。  
  
 [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 提供方法，讓主應用程式指定原則發生失敗和逾時所要採取的動作。  
  
 [ICLRProbingAssemblyEnum 介面](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 提供方法，讓主應用程式，以取得組件探查的身分識別使用而不需要建立，或了解該身分識別是 CLR 中，內部的組件的身分識別資訊。  
  
 [ICLRReferenceAssemblyEnum 介面](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 提供方法，讓主應用程式管理的檔案或組件的身分識別資料，而不需要建立，或了解這些身分識別是 CLR 中，內部的資料流所參考的組件集。  
  
 [ICLRRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 提供功能類似於[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)，以其他方法設定的主控件控制介面。  
  
 [ICLRSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 提供方法來取得要求的工作的相關資訊，及偵測死結的同步處理實作中的主機。  
  
 [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 提供方法，讓主應用程式提出要求的 clr 中，或以用於 CLR 有關相關聯的工作提供通知。  
  
 [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 提供方法，讓主應用程式明確要求 CLR 建立新的工作、 取得目前執行的工作，以及設定地理的語言和文化特性的工作。  
  
 [ICLRValidator 介面](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 提供方法來驗證的可攜式執行檔 (PE) 映像和報告驗證錯誤。  
  
 [ICorConfiguration 介面](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 提供用於設定 CLR 方法。  
  
 [ICorThreadpool 介面](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 提供方法來存取執行緒集區。  
  
 [IDebuggerInfo 介面](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 提供方法來取得有關偵錯服務的狀態資訊。  
  
 [IDebuggerThreadControl 介面](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 提供方法來通知主機有關封鎖和解除封鎖執行緒的偵錯服務。  
  
 [IGCHost 介面](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。  
  
 [IGCHost2 介面](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 提供[SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法，讓主應用程式來設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大值大於`DWORD`。  
  
 [IGCHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 提供方法，以允許要求的主機，若要變更的虛擬記憶體限制的記憶體回收行程。  
  
 [IGCThreadControl 介面](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 提供方法來參與，否則記憶體回收會封鎖執行緒的排程。  
  
 [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 提供方法，讓主應用程式指定的 CLR 或由主機載入的組件集合。  
  
 [IHostAssemblyStore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 提供方法，讓主應用程式載入組件和模組與 CLR 無關。  
  
 [IHostAutoEvent 介面](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 提供由主機實作的自動重設事件的表示法。  
  
 [IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 提供對於設定載入的組件，以及判斷哪些裝載介面主應用程式支援的方法。  
  
 [IHostCrst 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 可做為執行緒的關鍵區段之主機的表示法。  
  
 [IHostGCManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 提供方法，以通知主機實作的 CLR 記憶體回收機制中的事件。  
  
 [IHostIoCompletionManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 提供讓 CLR 主機所提供的 I/O 完成連接埠與互動的方法。  
  
 [IHostMalloc 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 提供 CLR 從透過主控件堆積要求更細緻的配置方法。  
  
 [IHostManualEvent 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 提供手動重設事件的表示主機的實作。  
  
 [IHostMemoryManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 提供 CLR 進行透過主應用程式，而不是使用標準的 Win32 虛擬記憶體函式的虛擬記憶體要求的方法。  
  
 [IHostPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 提供方法，通知主應用程式中的案例中的 CLR 執行的動作會中止，逾時或失敗。  
  
 [IHostSecurityContext 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 可讓 CLR 維護主機所實作的安全性內容資訊。  
  
 [IHostSecurityManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 提供方法，以啟用存取權，以及控制目前執行中執行緒的安全性內容。  
  
 [IHostSemaphore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 提供由主機實作的號誌的表示法。  
  
 [IHostSyncManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 提供 CLR 呼叫主應用程式，而不是使用 Win32 同步處理函式來建立同步處理原始物件的方法。  
  
 [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 提供讓 CLR 與主應用程式管理工作進行通訊的方法。  
  
 [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 提供啟用 CLR，才能透過主應用程式，而不是使用標準的作業系統執行緒或 fiber 函式的工作使用的方法。  
  
 [IHostThreadPoolManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 提供 clr 來設定執行緒集區，以及執行緒集區的工作項目佇列的方法。  
  
 [IManagedObject 介面](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 提供方法來控制受管理的物件。  
  
 "IObjectHandle"  
 提供從間接取值的解除包裝傳值方式封送處理物件的方法。  
  
 [ITypeName 介面](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 提供方法來取得型別名稱資訊。 （此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。  
  
 [ITypeNameBuilder 介面](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 提供方法來建置型別名稱。 （此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。  
  
 [ITypeNameFactory 介面](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 提供方法來解構類型名稱。 （此介面支援.NET Framework 基礎結構的而且不是直接從您的程式碼使用）。  
  
 「 IValidator"  
 提供方法來驗證的可攜式執行檔 (PE) 映像和報告驗證錯誤。  
  
## <a name="related-sections"></a>相關章節  
 [已被取代的 CLR 裝載介面和 Coclass](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 包含說明.NET Framework 1.0 和 1.1 版中提供裝載介面主題。  
  
 [.NET Framework 4 和 4.5 中新增的 CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 包含的主題將描述中所提供的裝載介面[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。
