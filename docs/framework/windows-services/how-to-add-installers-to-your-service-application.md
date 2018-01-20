---
title: "如何：加入 Installer 至服務應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 15487d4311f896aa09c1c7712292058086a49b50
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-installers-to-your-service-application"></a>如何：加入 Installer 至服務應用程式
Visual Studio 隨附安裝的元件，可將其與您的服務應用程式相關聯的資源。 安裝元件登錄的方法，它可以安裝，並讓服務控制管理員知道服務存在於的系統上的個別服務。 當您使用的服務應用程式時，您可以自動將適當的安裝程式新增至您的專案屬性 視窗中選取的連結。  
  
> [!NOTE]
>  您的服務的屬性值是從服務類別複製到安裝程式類別。 如果您更新服務類別上的屬性值，它們不會自動更新的安裝程式中。  
  
 當您將安裝程式加入您的專案，新的類別 (其中，根據預設，名為`ProjectInstaller`) 專案和適當的安裝，在其中建立元件的執行個體中建立。 所有安裝元件的中心點的這個類別是您的專案需要。 例如，如果您將第二個服務加入至您的應用程式，然後按一下 加入安裝程式連結，第二個安裝程式無法建立類別;相反地，第二個服務需要額外的安裝元件會加入至現有的類別。  
  
 您不需要任何特殊的安裝程式正確安裝程式服務中編碼方式。 不過，您偶爾可能需要以修改安裝程式的內容，如果您需要加入特殊功能的安裝程序。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-add-installers-to-your-service-application"></a>若要加入 installer 至服務應用程式  
  
1.  在**方案總管 中**，存取**設計**檢視您要將安裝元件服務。  
  
2.  本身，而不是它的任何內容，請按一下設計工具，以選取服務的背景。  
  
3.  與設計工具取得焦點時，按一下滑鼠右鍵，然後按一下**加入安裝程式**。  
  
     新的類別， `ProjectInstaller`，和兩個安裝元件，<xref:System.ServiceProcess.ServiceProcessInstaller>和<xref:System.ServiceProcess.ServiceInstaller>，元件會複製到服務，會加入至您的專案，並屬性值。  
  
4.  按一下<xref:System.ServiceProcess.ServiceInstaller>元件，並確認值<xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>屬性設定為相同的值<xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>本身在服務上的屬性。  
  
5.  若要判斷您的服務啟動的方式，請按一下<xref:System.ServiceProcess.ServiceInstaller>元件並設定<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>屬性設為適當值。  
  
    |值|結果|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|安裝之後，必須手動啟動服務。 如需詳細資訊，請參閱[如何： 啟動服務](../../../docs/framework/windows-services/how-to-start-services.md)。|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|服務將會自行啟動時重新啟動電腦。|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|無法啟動服務。|  
  
6.  若要判斷您的服務將在其中執行的安全性內容，請按一下<xref:System.ServiceProcess.ServiceProcessInstaller>元件，並設定適當的屬性值。 如需詳細資訊，請參閱[How to： 指定服務的安全性內容](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)。  
  
7.  覆寫任何您要執行自訂處理的方法。  
  
8.  在您的專案中每個其他服務執行步驟 1 到 7。  
  
    > [!NOTE]
    >  針對每個專案中的其他服務，您必須加入額外<xref:System.ServiceProcess.ServiceInstaller>元件在專案的`ProjectInstaller`類別。 <xref:System.ServiceProcess.ServiceProcessInstaller>三個步驟中加入元件適用於所有專案中的個別服務安裝程式。  
  
## <a name="see-also"></a>請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [如何：安裝和解除安裝服務](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [如何：啟動服務](../../../docs/framework/windows-services/how-to-start-services.md)  
 [如何：指定服務的安全性內容](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
