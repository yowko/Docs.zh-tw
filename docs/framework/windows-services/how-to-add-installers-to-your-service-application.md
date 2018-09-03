---
title: 如何：加入 Installer 至服務應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
author: ghogen
manager: douge
ms.openlocfilehash: 77f41e696fed3d33282b6437e99129fda9e209e9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43472016"
---
# <a name="how-to-add-installers-to-your-service-application"></a>如何：加入 Installer 至服務應用程式
Visual Studio 隨附安裝元件，可安裝與您服務應用程式相關聯的資源。 安裝元件會在其安裝所在的系統上註冊個別服務，並讓服務控制管理員知道服務的存在。 當您使用服務應用程式時，可以選取 [屬性] 視窗中的連結，以便自動將適當的安裝程式加入您的專案。  
  
> [!NOTE]
>  適用於服務的屬性值會從服務類別複製到安裝程式類別。 如果您更新服務類別上的屬性值，不會在安裝程式中自動更新它們。  
  
 當您將安裝程式加入至專案時，新的類別 (預設命名為 `ProjectInstaller`) 會建立於專案中，並在其中建立適當安裝元件的執行個體。 此類別可用來作為專案所需全部安裝元件的中心點。 例如，如果您將第二個服務加入至應用程式，然後按一下 [加入安裝程式] 連結，並不會建立第二個安裝程式類別；而是要將第二個服務所需的額外安裝元件加入至現有類別。  
  
 您不需要在安裝程式內進行任何特殊編碼，即可正確安裝您的服務。 不過，如果您需要將特殊功能加入至安裝程序，偶爾可能需要修改安裝程式的內容。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-add-installers-to-your-service-application"></a>將安裝程式加入服務應用程式  
  
1.  在 [方案總管] 中，針對您想要加入安裝元件的服務，存取服務的 [設計] 檢視。  
  
2.  按一下設計工具的背景以選取服務本身，而不是它的任何內容。  
  
3.  當設計工具取得焦點時，以滑鼠右鍵按一下，然後按一下 [加入安裝程式]。  
  
     隨即會在您的專案中加入一個新類別 (`ProjectInstaller`) 和兩個安裝元件 (<xref:System.ServiceProcess.ServiceProcessInstaller> 與 <xref:System.ServiceProcess.ServiceInstaller>)，並將服務的屬性值複製到元件。  
  
4.  按一下 <xref:System.ServiceProcess.ServiceInstaller> 元件，並確認已將 <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> 屬性的值設定為與服務本身 <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> 屬性相同的值。  
  
5.  若要決定服務啟動方式，按一下 <xref:System.ServiceProcess.ServiceInstaller> 元件，並將 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性設定為適當的值。  
  
    |值|結果|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|服務必須在安裝之後手動啟動。 如需詳細資訊，請參閱[如何：啟動服務](../../../docs/framework/windows-services/how-to-start-services.md)。|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|服務將在電腦重新開機時自行啟動。|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|無法啟動服務。|  
  
6.  若要決定服務將在其中執行的安全性內容，按一下 <xref:System.ServiceProcess.ServiceProcessInstaller> 元件，並設定適當的屬性值。 如需詳細資訊，請參閱[如何：指定服務的安全性內容](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)。  
  
7.  覆寫任何您需要為其執行自訂處理的方法。  
  
8.  針對專案中的每個額外服務執行步驟 1 到 7。  
  
    > [!NOTE]
    >  針對專案中的每個額外服務，您必須在專案的 `ProjectInstaller` 類別中加入額外的 <xref:System.ServiceProcess.ServiceInstaller> 元件。 在步驟三加入的 <xref:System.ServiceProcess.ServiceProcessInstaller> 元件適用於專案中所有的個別服務安裝程式。  
  
## <a name="see-also"></a>請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [如何：安裝和解除安裝服務](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [如何：啟動服務](../../../docs/framework/windows-services/how-to-start-services.md)  
 [如何：指定服務的安全性內容](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
