---
title: "如何：加入 Installer 至服務應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安裝元件, 加入至服務"
  - "安裝程式, 加入至服務"
  - "ServiceInstaller 類別, 將安裝程式加入至服務"
  - "ServiceProcessInstaller 類別, 將安裝程式加入至服務"
  - "服務, 加入安裝程式"
  - "Windows 服務應用程式, 加入安裝程式"
  - "Windows 服務應用程式, 部署"
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 14
---
# 如何：加入 Installer 至服務應用程式
Visual Studio 隨附一些安裝元件，這些元件可以安裝與您的服務應用程式相關聯的資源。  安裝元件會在安裝服務的系統中為每一個服務進行註冊，並讓 \[服務控制管理員\] 知道服務的存在。  當您使用服務應用程式時，可以在 \[屬性\] 視窗中選取將適當的安裝程式自動加入至專案的連結。  
  
> [!NOTE]
>  服務的屬性值會從服務類別複製到安裝程式類別中。  如果您更新服務類別中的屬性值，將不會自動更新安裝程式中的屬性值。  
  
 當您將安裝程式加入專案中時，會在專案中建立新類別 \(預設情況下，稱為 `ProjectInstaller`\)，並在其中建立適當的安裝元件執行個體。  這個類別是您的專案所需的所有安裝元件的中心點。  例如，如果將第二個服務加入您的應用程式中，並按一下 \[加入安裝程式\] 連結，並不會建立第二個安裝程式類別，而是會將第二個服務所需的其他安裝元件加入至現有的類別中。  
  
 您不需要在安裝程式中使用任何特定的編碼方式，就可以正確地安裝服務。  但是，如果您需要將特定的功能加入安裝過程中，可能需要修改安裝程式的內容。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要將安裝程式加入您的服務應用程式  
  
1.  在 \[**方案總管**\] 中，存取您希望加入安裝元件之服務的 \[**設計**\] 檢視。  
  
2.  按一下設計工具的背景 \(Background\) 來選取服務本身 \(而不是它的內容\)。  
  
3.  設計工具取得焦點時，以滑鼠右鍵按一下，再按 \[**加入安裝程式**\]。  
  
     新類別 \(`ProjectInstaller`\) 和兩個安裝元件 \(<xref:System.ServiceProcess.ServiceProcessInstaller> 和 <xref:System.ServiceProcess.ServiceInstaller>\) 會加入至您的專案，服務的屬性值則會被複製到元件中。  
  
4.  按一下 <xref:System.ServiceProcess.ServiceInstaller> 元件，並確認 <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> 屬性值是設定為和服務本身的 <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> 屬性相同的值。  
  
5.  若要決定如何啟動服務，請按一下 <xref:System.ServiceProcess.ServiceInstaller> 元件，並將 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性值設定為適當的值。  
  
    |值|結果|  
    |-------|--------|  
    |<xref:System.ServiceProcess.ServiceStartMode>|服務安裝後必須手動啟動。  如需詳細資訊，請參閱 [如何：啟動服務](../../../docs/framework/windows-services/how-to-start-services.md)。|  
    |<xref:System.ServiceProcess.ServiceStartMode>|每當電腦重新開機時，服務將會自行啟動。|  
    |<xref:System.ServiceProcess.ServiceStartMode>|無法啟動服務。|  
  
6.  若要決定在哪一個安全性內容中執行服務，請按一下 <xref:System.ServiceProcess.ServiceProcessInstaller> 元件，並設定適當的屬性值。  如需詳細資訊，請參閱 [如何：指定服務的安全性內容](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)。  
  
7.  覆寫任何需要執行自訂處理的方法。  
  
8.  針對專案中的每一個其他服務執行步驟 1 到步驟 7。  
  
    > [!NOTE]
    >  對於專案中的每一個額外服務，您必須將額外的 <xref:System.ServiceProcess.ServiceInstaller> 元件加入至專案的 `ProjectInstaller` 類別。  步驟 3 所加入的 <xref:System.ServiceProcess.ServiceProcessInstaller> 元件，會配合專案中每一個服務安裝程式運作。  
  
## 請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [如何：安裝及解除安裝服務](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)   
 [如何：啟動服務](../../../docs/framework/windows-services/how-to-start-services.md)   
 [如何：指定服務的安全性內容](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)