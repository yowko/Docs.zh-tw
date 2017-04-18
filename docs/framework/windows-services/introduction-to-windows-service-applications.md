---
title: "Windows 服務應用程式簡介 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ServiceController"
helpviewer_keywords: 
  - "架構服務, 建立服務"
  - "OnContinue 方法"
  - "OnPause 方法"
  - "OnStop 方法"
  - "Service 類別, Windows 服務應用程式"
  - "服務狀態"
  - "ServiceController 元件, 關於 Windows 服務"
  - "服務, 關於服務"
  - "服務, 存留期"
  - "服務, 狀態"
  - "WaitForStatus 方法"
  - "Win32OwnProcess 服務類型"
  - "Win32ShareProcess 服務類型"
  - "Windows 服務應用程式, 關於 Windows 服務應用程式"
  - "Windows 服務應用程式, 部署"
  - "Windows 服務應用程式, 存留期"
ms.assetid: 1b1b5e67-3ff3-40c0-8154-322cfd6ef0ae
caps.latest.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 17
---
# Windows 服務應用程式簡介
Microsoft Windows 服務，也就是先前的 NT 服務，可讓您建立長期執行的應用程式，在應用程式本身的 Windows 工作階段 \(Session\) 中執行。  這些服務可以在電腦啟動時自動啟動，也可以暫停或重新啟動，都不會顯示任何使用者介面。  這些功能使得服務非常適合在伺服器中使用，或每當需要不干擾使用同一部電腦之其他使用者的長期執行功能時使用。  您也可以在不同於登入使用者或預設電腦帳戶的特定使用者帳戶的安全性內容下執行服務。  如需服務和 Windows 工作階段的詳細資訊，請參閱 MSDN Library 中的 Windows SDK 文件。  
  
 您可以輕鬆地建立應用程式，並將其安裝成為服務。  例如，假設您希望監視效能計數器資料並反應臨界值。  您可以撰寫接聽 \(Listen\) 效能計數器資料的 Windows 服務應用程式、部署此應用程式並開始收集和分析資料。  
  
 您可以將服務建立為 Microsoft Visual Studio 專案，在其中定義程式碼，以便控制可以傳送給服務的命令，以及收到這些命令時應該採取的動作。  可以傳送給服務的命令包含啟動、暫停、繼續和停止服務，而且您也可以執行自訂命令。  
  
 當您建立並建置 \(Build\) 應用程式後，就可以執行命令列公用程式 InstallUtil.exe 並傳遞服務可執行檔的路徑，安裝此應用程式。  之後您可以利用 \[**服務控制管理員**\] 來啟動、停止、暫停、繼續和設定您的服務。  您也可以在 \[**伺服器總管**\] 的 \[**服務**\] 節點中，或利用 <xref:System.ServiceProcess.ServiceController> 類別，完成許多相同的工作。  
  
## 服務應用程式和其他 Visual Studio 應用程式的比較  
 服務應用程式的運作有幾方面不同於許多其他的專案類型，如下所示：  
  
-   服務應用程式專案所建立的編譯可執行檔必須在專案能夠以有意義的方式運作前安裝在伺服器中。  您不能按下 F5 或 F11 偵錯或執行服務應用程式，也不能立即執行服務或逐步執行程式碼。  而是必須安裝並啟動服務，再附加偵錯工具到服務的處理序 \(Process\) 中。  如需詳細資訊，請參閱[如何：偵錯 Windows 服務應用程式](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)。  
  
-   和某些類型的專案不同的是，您必須為服務應用程式建立安裝元件。  安裝元件負責在伺服器中安裝和註冊服務，並在 Windows 的 \[**服務控制管理員**\] 中建立服務項目。  如需詳細資訊，請參閱[如何：加入 Installer 至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。  
  
-   服務應用程式的 `Main` 方法必須為專案所包含的服務發出 Run 命令。  `Run` 方法會將服務載入至適當伺服器的 \[**服務控制管理員**\] 中。  如果您使用 \[**Windows 服務**\] 專案範本，則會自動為您撰寫這個方法。  請注意，載入服務和啟動服務是兩回事。  如需詳細資訊，請參閱下列＜服務的存留期＞一節。  
  
-   Windows 服務應用程式在不同的視窗型工作站 \(Window Station\) 中執行，而不是在登入使用者的互動式工作站 \(Interactive Station\) 上執行。  視窗工作站是安全物件，其中包含剪貼簿、一組全域元素和一組桌面物件。  由於 Windows 服務的工作站不是互動式工作站，所以將無法看見由 Windows 服務應用程式內引發的對話方塊，而且可能造成程式停止回應。  同樣地，錯誤訊息應該記錄在 Windows 事件記錄檔中，而不是產生在使用者介面中。  
  
     .NET Framework 支援的 Windows 服務類別並不支援與互動式工作站 \(也就是登入使用者\) 的互動。  .NET Framework 也不包含表示工作站和桌面的類別。  如果您的 Windows 服務必須與其他工作站互動，則需要存取 Unmanaged Windows API。  如需詳細資訊，請參閱 Windows SDK 文件。  
  
     Windows 服務與使用者或其他工作站的互動必須仔細經過設計以包含案例，例如沒有登入使用者，或是使用者具有未預期的桌面物件組。  在某些情況中，可能撰寫在使用者控制下執行的 Windows 應用程式會更為恰當。  
  
-   Windows 服務應用程式會在它們自己的安全性內容中執行，並在使用者登入安裝服務的 Windows 電腦前就已經啟動。  您應該仔細地規劃服務要在那個使用者帳戶中執行；在系統帳戶下執行的服務所擁有的權限高於使用者帳戶。  
  
## 服務的存留期  
 服務會在它的存留期中經過幾個內部的狀態。  首先，會將服務安裝在將執行該服務的系統中。  這個處理序會執行服務專案的安裝程式，並將服務載入該電腦的 \[**服務控制管理員**\] 中。  \[**服務控制管理員**\] 是 Windows 提供給管理服務的集中式公用程式。  
  
 載入服務後，必須啟動該服務。  啟動服務讓它可以開始運作。  您可以藉由呼叫 <xref:System.ServiceProcess.ServiceController.Start%2A> 方法，從 \[**服務控制管理員**\]、\[**伺服器總管**\] 或程式碼啟動服務。  <xref:System.ServiceProcess.ServiceController.Start%2A> 方法會將處理傳遞給應用程式的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法，並處理您在方法中定義的程式碼。  
  
 執行中的服務可以無限期地存在於這個狀態中，直到停止或暫停該服務，或直到電腦關機為止。  服務可以存在於三個基本狀態的其中之一：<xref:System.ServiceProcess.ServiceControllerStatus>、<xref:System.ServiceProcess.ServiceControllerStatus> 或 <xref:System.ServiceProcess.ServiceControllerStatus>。  服務也可以回報暫止命令的狀態：<xref:System.ServiceProcess.ServiceControllerStatus>、<xref:System.ServiceProcess.ServiceControllerStatus>、<xref:System.ServiceProcess.ServiceControllerStatus> 或 <xref:System.ServiceProcess.ServiceControllerStatus>。  這些狀態指示已經發出命令，例如暫停執行中服務的命令，但是還沒有執行該命令。  您可以查詢 <xref:System.ServiceProcess.ServiceController.Status%2A> 來判斷服務所處的狀態，或利用 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> 在發生這些狀態任一項時執行動作。  
  
 您可以從 \[**服務控制管理員**\]、\[**伺服器總管**\] 或在程式碼中呼叫方法，以暫停、停止或繼續服務。  每一個動作都可以呼叫服務中的相關程序 \(<xref:System.ServiceProcess.ServiceBase.OnStop%2A>、<xref:System.ServiceProcess.ServiceBase.OnPause%2A> 或 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>\)，您可以在其中定義服務改變狀態時要執行的其他處理。  
  
## 服務類型  
 您可以使用 .NET Framework 在 Visual Studio 中建立兩種服務類型。  屬於處理序中唯一的服務，會指定為 <xref:System.ServiceProcess.ServiceType> 類型。  和其他服務共用處理序的服務，則指定為 <xref:System.ServiceProcess.ServiceType> 類型。  您可以查詢 <xref:System.ServiceProcess.ServiceController.ServiceType%2A> 屬性，藉以擷取服務類型。  
  
 如果您查詢非 Visual Studio 所建立的現有服務，有時候您會看到其他的服務類型。  如需這些服務的詳細資訊，請參閱 <xref:System.ServiceProcess.ServiceType>。  
  
## 服務和 ServiceController 元件  
 <xref:System.ServiceProcess.ServiceController> 元件用以連接已安裝的服務並且管理其狀態；利用 <xref:System.ServiceProcess.ServiceController> 元件，您可以啟動和停止服務、暫停和繼續其運作，並傳送自訂命令給服務。  但是，當您建立服務應用程式時，並不需要使用 <xref:System.ServiceProcess.ServiceController> 元件。  事實上，在大多數情況下，<xref:System.ServiceProcess.ServiceController> 元件應該存在於定義服務之 Windows 服務應用程式之外的另一個應用程式中。  
  
 如需詳細資訊，請參閱<xref:System.ServiceProcess.ServiceController>。  
  
## 需求  
  
-   服務必須在 \[**Windows 服務**\] 應用程式專案或另一個啟用 .NET Framework 的專案中建立，而這個專案建置時會建立 .exe 檔案並繼承自 <xref:System.ServiceProcess.ServiceBase> 類別。  
  
-   包含 Windows 服務的專案，必須有專案和其服務的安裝元件。  在 \[**屬性**\] 視窗中可以輕鬆地完成這個工作。  如需詳細資訊，請參閱[如何：加入 Installer 至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。  
  
## 請參閱  
 [Windows 服務應用程式](../../../docs/framework/windows-services/index.md)   
 [服務應用程式的程式設計架構](../../../docs/framework/windows-services/service-application-programming-architecture.md)   
 [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)   
 [如何：安裝及解除安裝服務](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)   
 [如何：啟動服務](../../../docs/framework/windows-services/how-to-start-services.md)   
 [如何：偵錯 Windows 服務應用程式](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)   
 [逐步解說：在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)   
 [如何：加入 Installer 至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)