---
title: "Windows 服務應用程式簡介"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 613107a13820ad71b854dcba93f21c41f2a5fa5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="introduction-to-windows-service-applications"></a>Windows 服務應用程式簡介
Microsoft Windows 服務，之前稱為 NT 服務可讓您建立自己的 Windows 工作階段中執行的長時間執行可執行應用程式。 當電腦開機時，自動啟動這些服務也可以暫停或重新啟動，且並未顯示任何使用者介面。 這些功能可讓服務特別適用於在伺服器上，或者每當您需要長時間執行的功能，不會干擾正在同一部電腦的其他使用者。 您也可以在不同於登入使用者的特定使用者帳戶或預設電腦帳戶的安全性內容中執行服務。 如需有關服務和 Windows 工作階段的詳細資訊，請參閱 Windows SDK 的文件。  
  
 您可以建立的應用程式，安裝為服務，輕鬆建立服務。 例如，假設您想要監視的效能計數器資料，並反應臨界值。 您無法撰寫 Windows 服務應用程式所接聽的效能計數器資料、 部署應用程式，以及開始收集和分析資料。  
  
 您建立您的服務，為 Microsoft Visual Studio 專案時，定義在其中控制哪些命令的程式碼可以傳送到服務，並會在收到這些命令時，應該採取什麼動作。 可以傳送至服務的命令包括啟動、 暫停、 繼續和停止服務。您也可以執行自訂命令。  
  
 您建立並建置應用程式之後，您可以以執行 InstallUtil.exe 的命令列公用程式，並將路徑傳遞至服務的可執行檔來進行安裝。 然後您可以使用**服務控制管理員**來啟動、 停止、 暫停、 繼續及設定您的服務。 您也可以完成相同工作中的許多**服務**節點**伺服器總管**或使用<xref:System.ServiceProcess.ServiceController>類別。  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>服務應用程式與Visual Studio 中的其他應用程式  
 服務應用程式仍可與幾種方式的許多其他專案類型不同：  
  
-   建立服務應用程式專案的已編譯可執行檔必須安裝在伺服器上，然後專案可以有意義的方式運作。 您無法偵錯或執行服務應用程式，按下 F5 或 F11;其程式碼，您無法立即執行的服務或步驟。 相反地，您必須安裝並啟動您的服務並再將偵錯工具附加至服務的程序。 如需詳細資訊，請參閱[如何： 偵錯 Windows 服務應用程式](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)。  
  
-   不同於某些類型的專案，您必須建立服務應用程式的安裝元件。 安裝元件安裝和註冊的伺服器上的服務，並建立您的服務項目，使用 Windows**服務控制管理員**。 如需詳細資訊，請參閱[如何： 加入至您的服務應用程式的安裝程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。  
  
-   `Main`方法的服務應用程式必須發行服務的 [執行] 命令專案包含。 `Run`方法會為服務載入**服務控制管理員**適當伺服器上。 如果您使用**Windows 服務**專案範本，這個方法會為您自動寫入。 請注意，載入服務無法啟動服務相同的動作。 「 服務的存留期 」 下面的如需詳細資訊，請參閱。  
  
-   在不同的視窗工作站比互動式登入使用者的工作站中，執行 Windows 服務應用程式。 視窗工作站是安全的物件，其中包含剪貼簿、 一組通用的元素和桌面的物件群組。 Windows 服務的站台不是互動式的站台，因為對話方塊所產生的一種 Windows 服務應用程式不會看到，並可能會造成程式停止回應。 同樣地，錯誤訊息應該登入 Windows 事件記錄檔，而使用者介面中引發。  
  
     .NET Framework 所支援的 Windows 服務類別不支援互動式電台，也就是登入的使用者互動。 .NET Framework 也不包含代表站台和桌上型電腦的類別。 如果您的 Windows 服務必須與其他站台互動，您必須存取不受管理的 Windows API。 如需詳細資訊，請參閱 Windows SDK 的文件。  
  
     與使用者或其他站台的服務必須仔細地設計以包含這類案例那里沒有登入的使用者或使用者具有未預期的桌面物件組之 windows 互動。 在某些情況下，它可能會更加適合撰寫 Windows 應用程式之使用者的控制下執行的程式碼。  
  
-   Windows 服務應用程式在使用者的安全性內容中執行，並啟動之前在使用者登入安裝所在的 Windows 電腦。 您應該仔細地規劃哪些使用者帳戶，來執行; 內的服務在系統帳戶下執行的服務有多個權限和權限與使用者帳戶。  
  
## <a name="service-lifetime"></a>服務的存留期  
 服務會在其存留期間經歷數個內部狀態。 首先，它會在其執行的系統上安裝此服務。 此程序執行的安裝程式服務專案，並載入到服務**服務控制管理員**該電腦。 **服務控制管理員**是中央管理服務的 Windows 所提供的公用程式。  
  
 已載入該服務之後，它必須啟動。 正在啟動服務，可讓它開始運作。 您可以啟動服務，以從**服務控制管理員**，從**伺服器總管**，藉由呼叫的程式碼之間來回<xref:System.ServiceProcess.ServiceController.Start%2A>方法。 <xref:System.ServiceProcess.ServiceController.Start%2A>方法會處理傳遞至應用程式的<xref:System.ServiceProcess.ServiceBase.OnStart%2A>方法並處理您已那里定義任何程式碼。  
  
 執行中服務的存在處於此狀態中，直到它停止或暫停，或是直到電腦關機。 服務可以存在於三個基本狀態之一： <xref:System.ServiceProcess.ServiceControllerStatus.Running>， <xref:System.ServiceProcess.ServiceControllerStatus.Paused>，或<xref:System.ServiceProcess.ServiceControllerStatus.Stopped>。 服務也可以報告的暫止命令的狀態： <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>， <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>， <xref:System.ServiceProcess.ServiceControllerStatus.StartPending>，或<xref:System.ServiceProcess.ServiceControllerStatus.StopPending>。 這些狀態會指出命令已發出，例如命令，以暫停執行中的服務，但有不執行。 您可以查詢<xref:System.ServiceProcess.ServiceController.Status%2A>判斷何種狀態服務是在中，或使用<xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>執行動作，任何這兩種狀態時，就會發生。  
  
 您可以暫停、 停止或繼續從服務**服務控制管理員**，從**伺服器總管**，或藉由在程式碼中呼叫方法。 每個動作可以在服務中呼叫相關聯的程序 (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>， <xref:System.ServiceProcess.ServiceBase.OnPause%2A>，或<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>)，您可以定義服務的狀態變更時所要執行額外的處理中。  
  
## <a name="types-of-services"></a>類型的服務  
 有兩種類型的服務，您可以使用.NET Framework 的 Visual Studio 中建立。 會指派給服務的處理程序中唯一的服務類型<xref:System.ServiceProcess.ServiceType.Win32OwnProcess>。 會指派給另一個服務共用處理序的服務類型<xref:System.ServiceProcess.ServiceType.Win32ShareProcess>。 您可以藉由查詢擷取的服務類型<xref:System.ServiceProcess.ServiceController.ServiceType%2A>屬性。  
  
 如果查詢未建立 Visual Studio 中的現有服務，有時可能會看到其他服務類型。 如需這些的詳細資訊，請參閱<xref:System.ServiceProcess.ServiceType>。  
  
## <a name="services-and-the-servicecontroller-component"></a>服務和 ServiceController 元件  
 <xref:System.ServiceProcess.ServiceController>元件是用來連接到已安裝的服務和操作其狀態，使用<xref:System.ServiceProcess.ServiceController>元件，啟動和停止服務、 暫停和繼續其正常運作，即可將自訂命令傳送至服務。 不過，您不需要使用<xref:System.ServiceProcess.ServiceController>當您建立服務應用程式的元件。 事實上，在大部分情況下您<xref:System.ServiceProcess.ServiceController>元件應存在於不同的應用程式定義服務的 Windows 服務應用程式。  
  
 如需詳細資訊，請參閱<xref:System.ServiceProcess.ServiceController>。  
  
## <a name="requirements"></a>需求  
  
-   服務也必須在建立**Windows 服務**應用程式專案或其他.NET Framework 功能，以建立.exe 檔建置時，並繼承自專案<xref:System.ServiceProcess.ServiceBase>類別。  
  
-   專案包含 Windows 服務必須有專案和其服務的安裝元件。 這可以輕鬆地完成從**屬性**視窗。 如需詳細資訊，請參閱[如何： 加入至您的服務應用程式的安裝程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。  
  
## <a name="see-also"></a>請參閱  
 [Windows 服務應用程式](../../../docs/framework/windows-services/index.md)  
 [服務應用程式的程式設計架構](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [如何：安裝和解除安裝服務](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [如何：啟動服務](../../../docs/framework/windows-services/how-to-start-services.md)  
 [如何：偵錯 Windows 服務應用程式](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [逐步解說：在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 [如何：將 Installer 新增至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
