---
title: 如何：啟動服務
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 47e27f579c0ed7d1be0b061bc6e79bba0c060abb
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-start-services"></a>如何：啟動服務
安裝服務之後，它必須啟動。 開始呼叫<xref:System.ServiceProcess.ServiceBase.OnStart%2A>服務類別上的方法。 通常，<xref:System.ServiceProcess.ServiceBase.OnStart%2A>方法來定義服務將會執行實際工作。 服務啟動之後，它會保持有效，直到以手動方式暫停或停止。  
  
 服務可以設定要自動或手動啟動。 安裝所在的電腦已重新開機，或第一次開啟時，將會啟動時自動啟動服務。 使用者必須啟動服務，以手動方式啟動。  
  
> [!NOTE]
>  根據預設，使用 Visual Studio 建立的服務會設定為手動啟動。  
  
 有數種方式，您可以手動啟動服務，從**伺服器總管**，從**服務控制管理員**，或從程式碼使用的元件呼叫<xref:System.ServiceProcess.ServiceController>。  
  
 您設定<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>屬性<xref:System.ServiceProcess.ServiceInstaller>類別以決定服務是否應該在手動或自動啟動。  
  
### <a name="to-specify-how-a-service-should-start"></a>若要指定服務應該啟動的方式  
  
1.  建立您的服務之後, 加入必要的安裝它。 如需詳細資訊，請參閱[如何： 加入至您的服務應用程式的安裝程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。  
  
2.  在設計工具中，按一下您要使用服務的服務安裝程式。  
  
3.  在**屬性**視窗中，將<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>屬性，以下列其中之一：  
  
    |若要讓安裝程式服務|將此值設定|  
    |----------------------------------|--------------------|  
    |重新啟動電腦|**自動**|  
    |當明確的使用者動作啟動服務|**手動**|  
  
    > [!TIP]
    >  若要避免您的服務所完全啟動，您可以設定<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>屬性**已停用**。 如果您要將伺服器重新開機多次，而且想要節省時間而導致無法正常啟動正在啟動服務，您可以這樣做。  
  
    > [!NOTE]
    >  之後安裝您的服務，可以變更這些屬性和其他屬性。  
  
     有數種方式，您可以啟動的服務具有其<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>程序設定為**手動**— 從**伺服器總管**，從**Windows 服務控制管理員**，或從程式碼。 請務必注意所有這些方法實際上的內容中啟動服務**服務控制管理員**;**伺服器總管**和以程式設計方式啟動服務的實際管理控制站。  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>若要從 [伺服器總管] 中手動啟動服務  
  
1.  在**伺服器總管**，新增您想如果未列出的伺服器。 如需詳細資訊，請參閱 < 如何： 存取及初始化伺服器總管資料庫總管。  
  
2.  展開**服務** 節點，然後找出您想要啟動的服務。  
  
3.  以滑鼠右鍵按一下服務名稱，然後按一下**啟動**。  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>若要手動啟動服務從服務控制管理員  
  
1.  開啟**服務控制管理員**由下列其中一項動作：  
  
    -   在 Windows XP 和 2000 Professional，以滑鼠右鍵按一下**我的電腦**桌面，然後按一下**管理**。 在出現的對話方塊中，依序展開**服務和應用程式**節點。  
  
         \-或-  
  
    -   在 Windows Server 2003 和 Windows 2000 Server 中，按一下 **啟動**，指向 **程式**，按一下**系統管理工具**，然後按一下 **服務**.  
  
        > [!NOTE]
        >  在 Windows NT 4.0 版，您可以開啟此對話方塊中，從**控制台**。  
  
     您現在應該會看到您的服務中所列**服務**視窗的區段。  
  
2.  清單中選取您的服務，以滑鼠右鍵按一下，然後按**啟動**。  
  
### <a name="to-manually-start-a-service-from-code"></a>若要從程式碼中手動啟動服務  
  
1.  建立的執行個體<xref:System.ServiceProcess.ServiceController>類別，並將它設定為與您想要管理的服務互動。  
  
2.  呼叫 <xref:System.ServiceProcess.ServiceController.Start%2A> 方法啟動服務。  
  
## <a name="see-also"></a>另請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [如何：將 Installer 新增至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
