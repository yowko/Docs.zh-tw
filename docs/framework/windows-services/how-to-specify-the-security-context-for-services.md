---
title: 如何：指定服務的安全性內容
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
author: ghogen
manager: douge
ms.openlocfilehash: e3e5ad7dd44dcaf1593ac80bbe6d0a367964e4e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-security-context-for-services"></a>如何：指定服務的安全性內容
根據預設，服務會在不同的安全性內容以外的登入的使用者中執行。 預設的系統帳戶內容中執行的服務呼叫`LocalSystem`，讓他們擁有不同的存取權限與使用者的系統資源。 您可以變更此行為，以指定不同的使用者帳戶，您的服務應在其下執行。  
  
 管理設定的安全性內容<xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A>服務執行所在的處理序的屬性。 這個屬性可讓您將服務設定為四種帳戶類型之一：  
  
-   `User`這會使系統服務已安裝，且指定的網路; 上的單一使用者帳戶內容中執行時，有效的使用者名稱和密碼提示  
  
-   `LocalService`其中會做為沒有權限的使用者的本機電腦上，並提供匿名認證給任何遠端伺服器的帳戶內容中執行  
  
-   `LocalSystem`其中會提供延伸本機的權限，並顯示電腦的認證給任何遠端伺服器; 的帳戶內容中執行  
  
-   `NetworkService`其中會做為沒有權限的使用者的本機電腦上，並顯示電腦的認證給任何遠端伺服器的帳戶內容中執行。  
  
 如需詳細資訊，請參閱 <xref:System.ServiceProcess.ServiceAccount> 列舉。  
  
### <a name="to-specify-the-security-context-for-a-service"></a>若要指定服務的安全性內容  
  
1.  建立您的服務之後, 加入必要的安裝它。 如需詳細資訊，請參閱[如何： 加入至您的服務應用程式的安裝程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。  
  
2.  在設計工具中，存取`ProjectInstaller`類別，並按一下您要使用的服務的服務處理程序安裝程式。  
  
    > [!NOTE]
    >  每一個服務應用程式中，有至少兩個安裝元件中的`ProjectInstaller`類別 — 一個用於專案中，而每個服務應用程式包含一個安裝程式會安裝所有服務的程序。 在本例中，您想要選取<xref:System.ServiceProcess.ServiceProcessInstaller>。  
  
3.  在**屬性**視窗中，將<xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A>適當的值。  
  
## <a name="see-also"></a>另請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [如何：將 Installer 新增至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)
