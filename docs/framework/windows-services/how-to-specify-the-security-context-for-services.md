---
title: "如何：指定服務的安全性內容 | Microsoft Docs"
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
  - "內容, Visual Studio 安全性"
  - "安全性 [Visual Studio], 內容"
  - "安全性 [Visual Studio], 服務應用程式"
  - "ServiceInstaller 類別, 安全性內容"
  - "ServiceProcessInstaller 類別, 安全性內容"
  - "服務, 安全性"
  - "Windows 服務應用程式, 安全性"
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 10
---
# 如何：指定服務的安全性內容
根據預設，服務是在不同於登入使用者的安全性內容下執行。  服務是在稱為 `LocalSystem` 的預設系統帳戶內容下執行，這個帳戶會賦予它們不同於使用者的系統資源存取權限。  您可以改變此行為，指定服務應該在其他的使用者帳戶下執行。  
  
 您可以管理服務所執行處理序中的 <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> 屬性，設定安全性內容。  這個屬性可讓您將服務設定為下列四種帳戶類型之一：  
  
-   `User`，當服務在網路上單一使用者指定的帳戶內容中安裝和執行時，引發系統提示必須輸入有效的使用者名稱和密碼。  
  
-   `LocalService`，在當做本機電腦上沒有權限使用者的帳戶內容中執行，而且將匿名認證提供給任何遠端伺服器。  
  
-   `LocalSystem`，在帳戶中提供各種本機權限，而且將電腦的認證提供給任何遠端伺服器;  
  
-   `NetworkService`，在當做本機電腦上沒有權限使用者的帳戶內容中執行，而且將電腦的認證提供給任何遠端伺服器。  
  
 如需詳細資訊，請參閱 <xref:System.ServiceProcess.ServiceAccount> 列舉。  
  
### 指定服務的安全性內容  
  
1.  建立您的服務後，為它加入必要的安裝程式。  如需詳細資訊，請參閱[如何：加入 Installer 至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。  
  
2.  在設計工具中，存取 `ProjectInstaller` 類別並按一下您正在使用之服務的服務處理序安裝程式。  
  
    > [!NOTE]
    >  對每一個服務應用程式而言，`ProjectInstaller` 類別中至少有兩個安裝元件：負責安裝專案中所有服務的處理序，以及應用程式包含的每一個服務的安裝程式。  在這個例子中，您希望選取 <xref:System.ServiceProcess.ServiceProcessInstaller>。  
  
3.  在 \[**屬性**\] 視窗中，將 <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> 設定為適當值。  
  
## 請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [如何：加入 Installer 至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)   
 [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)