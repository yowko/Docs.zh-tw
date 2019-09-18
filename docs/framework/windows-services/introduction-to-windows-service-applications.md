---
title: Windows 服務應用程式簡介
ms.date: 03/30/2017
f1_keywords:
- ServiceController
helpviewer_keywords:
- Windows Service applications, deploying
- OnStop method
- OnPause method
- services, about services
- Service class, Windows Service applications
- framework services, creating services
- ServiceController components, about Windows services
- Win32OwnProcess service type
- services, lifetime
- OnContinue method
- Windows Service applications, about Windows Service applications
- services, states
- service states
- WaitForStatus method
- Win32ShareProcess service type
- Windows Service applications, lifetime
ms.assetid: 1b1b5e67-3ff3-40c0-8154-322cfd6ef0ae
author: ghogen
ms.openlocfilehash: 8ff1adaa025dc11417c3dcfdaf42ea203828be57
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053513"
---
# <a name="introduction-to-windows-service-applications"></a>Windows 服務應用程式簡介
Microsoft Windows 服務 (以前稱為 NT 服務) 讓您能夠建立長時間執行的應用程式，並使其在自己的 Windows 工作階段中執行。 這些服務可以在電腦開機時自動啟動、可以暫停和重新啟動，而且不會顯示任何使用者介面。 這些功能讓服務非常適合在伺服器上使用，或者，當您需要不會干擾其他在同一部電腦上工作的使用者且又長時間執行的功能時使用。 您也可以在特定使用者帳戶的安全性內容中執行服務，此使用者帳戶不同於登入的使用者帳戶或預設電腦帳戶。 如需服務和 Windows 工作階段的詳細資訊，請參閱 Windows SDK 文件。  
  
 您可以藉由建立要安裝為服務的應用程式，輕鬆地建立服務。 例如，假設您想要監視效能計數器資料並回應閾值。 您可以撰寫 Windows 服務應用程式來接聽效能計數器資料、部署應用程式，然後開始收集和分析資料。  
  
 您會以 Microsoft Visual Studio 專案來建立服務，在其中定義程式碼來控制可以傳送到服務的命令，以及在收到命令時應該採取的動作。 可傳送到服務的命令包括啟動、暫停、繼續和停止服務；您也可以執行自訂命令。  
  
 當您建立和建置應用程式之後，可執行命令列公用程式 InstallUtil.exe，並傳入服務可執行檔的路徑來進行安裝。 您接著可以使用**服務控制管理員**來啟動、停止、暫停、繼續及設定服務。 您也可以在 [伺服器總管] 的 [服務] 節點中完成這其中許多相同的工作，或是使用 <xref:System.ServiceProcess.ServiceController> 類別來完成。  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>服務應用程式相較於其他 Visual Studio 應用程式  
 服務應用程式的運作在某些方面有別於許多其他專案類型：  
  
- 服務應用程式專案所建立的已編譯可執行檔必須先安裝在伺服器上，然後專案才能正常地運作。 您無法按 F5 鍵或 F11 鍵來偵錯或執行服務應用程式；您無法立即執行服務或逐步執行其程式碼。 反之，您必須安裝並啟動服務，然後將偵錯工具附加到服務的處理序。 如需詳細資訊，請參閱[如何：偵錯 Windows 服務應用程式](how-to-debug-windows-service-applications.md)。  
  
- 不同於某些類型的專案，您必須為服務應用程式建立安裝元件。 安裝元件會在伺服器上安裝並註冊服務，以及使用 Windows **服務控制管理員**來建立服務項目。 如需詳細資訊，請參閱[如何：將安裝程式新增至服務應用程式](how-to-add-installers-to-your-service-application.md)。  
  
- 服務應用程式的 `Main` 方法必須針對專案所包含的服務發出 Run 命令。 `Run` 方法會將服務載入到適當伺服器上的**服務控制管理員**。 如果您使用 **Windows 服務**專案範本，即會自動撰寫這個方法。 請注意，載入服務與啟動服務不同。 如需詳細資訊，請參閱下方的「服務存留期」。  
  
- Windows 服務應用程式執行所在的視窗工作站，不同於登入使用者的互動式工作站。 視窗工作站是一個安全的物件，其中包含剪貼簿、一組通用元素，以及一個桌面物件群組。 由於 Windows 服務的工作站不是互動式工作站，因此看不到從 Windows 服務應用程式內引發的對話方塊，因而可能造成程式停止回應。 同樣地，錯誤訊息應該記錄於 Windows 事件記錄檔中，而不應在使用者介面中引發。  
  
     .NET Framework 所支援的 Windows 服務類別不支援與互動式工作站 (也就是登入的使用者) 進行互動。 .NET Framework 也不會包含代表工作站和桌面的類別。 如果您的 Windows 服務必須與其他工作站互動，您將需要存取非受控的 Windows API。 如需詳細資訊，請參閱 Windows SDK 文件。  
  
     Windows 服務與使用者或其他工作站的互動必須經過精心設計以包含如下的案例：沒有登入的使用者，或者使用者具備一組未預期的桌面物件。 在某些情況下，撰寫由使用者控制的 Windows 應用程式可能更為合適。  
  
- Windows 服務應用程式會在自己的安全性內容中執行，並在使用者登入安裝應用程式所在的 Windows 電腦之前便啟動。 您應該仔細規劃要在哪些使用者帳戶內執行服務；在系統帳戶下執行的服務，其權限會高於在使用者帳戶下執行的服務。  
  
## <a name="service-lifetime"></a>服務存留期  
 服務會在其存留期中會經歷數個內部狀態。 首先，服務會安裝於執行所在的系統上。 此流程會針對服務專案執行安裝程式，並將服務載入該電腦的**服務控制管理員**。 **服務控制管理員**是由 Windows 提供來管理服務的重要公用程式。  
  
 載入服務之後，必須加以啟動。 啟動服務即可讓它開始運作。 啟動服務的方式有三種：從**服務控制管理員**、從**伺服器總管**，或從程式碼中呼叫 <xref:System.ServiceProcess.ServiceController.Start%2A> 方法。 <xref:System.ServiceProcess.ServiceController.Start%2A> 方法會將處理傳遞到應用程式的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法，並處理您在該處定義的任何程式碼。  
  
 執行中的服務可以此狀態無限期存在，直到它停止或暫停，或是直到電腦關機為止。 服務可以下列三種基本狀態之一存在：<xref:System.ServiceProcess.ServiceControllerStatus.Running>、<xref:System.ServiceProcess.ServiceControllerStatus.Paused> 或 <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>。 服務也可以報告擱置命令的狀態：<xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>、<xref:System.ServiceProcess.ServiceControllerStatus.PausePending>、<xref:System.ServiceProcess.ServiceControllerStatus.StartPending> 或 <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>。 這些狀態指出已發出命令 (例如要暫停執行中服務的命令)，但尚未執行。 您可以查詢 <xref:System.ServiceProcess.ServiceController.Status%2A> 以判斷服務處於何種狀態，或者使用 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> 在發生這其中任一種狀態時執行動作。  
  
 暫停、停止或繼續執行服務的方式有三種：從**服務控制管理員**、從**伺服器總管**，或在程式碼中呼叫方法。 這其中的每個動作都可在服務中呼叫相關聯的程序 (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>、<xref:System.ServiceProcess.ServiceBase.OnPause%2A> 或 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>)，而您可以在其中定義要在服務變更狀態時所執行的額外處理。  
  
## <a name="types-of-services"></a>服務的類型  
 在 Visual Studio 中，使用 .NET Framework 可建立兩種類型的服務。 若服務是處理序中的唯一服務，即會為其指派 <xref:System.ServiceProcess.ServiceType.Win32OwnProcess> 類型。 若服務會與其他服務共用處理序，則會為其指派 <xref:System.ServiceProcess.ServiceType.Win32ShareProcess> 類型。 您可以藉由查詢 <xref:System.ServiceProcess.ServiceController.ServiceType%2A> 屬性來擷取服務類型。  
  
 如果您查詢尚未在 Visual Studio 中建立的現有服務，則可能會看到其他服務類型。 如需詳細資訊，請參閱 <xref:System.ServiceProcess.ServiceType>。  
  
## <a name="services-and-the-servicecontroller-component"></a>服務和 ServiceController 元件  
 <xref:System.ServiceProcess.ServiceController> 元件可用來連線到已安裝的服務並操控其狀態；使用 <xref:System.ServiceProcess.ServiceController> 元件可啟動和停止服務、暫停和繼續其運作，以及將自訂命令傳送到服務。 不過，當您建立服務應用程式時，不需要使用 <xref:System.ServiceProcess.ServiceController> 元件。 事實上，在大部分情況下，<xref:System.ServiceProcess.ServiceController> 元件所存在的應用程式，應該有別於定義服務的 Windows 服務應用程式。  
  
 如需詳細資訊，請參閱 <xref:System.ServiceProcess.ServiceController>。  
  
## <a name="requirements"></a>需求  
  
- 服務必須建立於 **Windows 服務**應用程式專案或其他已啟用 .NET Framework 的專案中，以便在建置時建立 .exe 檔並繼承自 <xref:System.ServiceProcess.ServiceBase> 類別。  
  
- 包含 Windows 服務的專案必須具備專案及其服務的安裝元件。 這可輕鬆地從 [屬性] 視窗來完成。 如需詳細資訊，請參閱[如何：將安裝程式新增至服務應用程式](how-to-add-installers-to-your-service-application.md)。  
  
## <a name="see-also"></a>另請參閱

- [Windows 服務應用程式](index.md)
- [服務應用程式的程式設計架構](service-application-programming-architecture.md)
- [如何：建立 Windows 服務](how-to-create-windows-services.md)
- [如何：安裝和解除安裝服務](how-to-install-and-uninstall-services.md)
- [如何：啟動服務](how-to-start-services.md)
- [如何：偵錯 Windows 服務應用程式](how-to-debug-windows-service-applications.md)
- [逐步解說：在元件設計工具中建立 Windows 服務應用程式](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
- [如何：將安裝程式新增至服務應用程式](how-to-add-installers-to-your-service-application.md)
