---
title: 作法：啟動服務
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: db66e8a264bc0381a2ff4689c4427047a158eb32
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336833"
---
# <a name="how-to-start-services"></a>作法：啟動服務
安裝服務之後，必須加以啟動。 從呼叫服務類別上的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法開始。 通常，<xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法會定義服務將執行的有用工作。 服務啟動之後，即會保持作用中，直到您以手動方式暫停或停止它為止。  
  
 服務可以設定為自動或手動啟動。 自動啟動的服務將在其安裝所在的電腦重新開機或第一次開啟時啟動。 使用者必須啟動以手動方式啟動的服務。  
  
> [!NOTE]
>  根據預設，使用 Visual Studio 建立的服務均會設定為以手動方式啟動。  
  
 有數種方式可讓您以手動方法啟動服務：從 [伺服器總管]、從 [服務控制管理員]，或從程式碼使用稱為 <xref:System.ServiceProcess.ServiceController> 的元件。  
  
 您會設定 <xref:System.ServiceProcess.ServiceInstaller> 類別上的 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性，以決定服務應手動或自動啟動。  
  
### <a name="to-specify-how-a-service-should-start"></a>指定啟動服務的方式  
  
1. 建立服務之後，為其加入必要的安裝程式。 如需詳細資訊，請參閱[如何：將安裝程式新增至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。  
  
2. 在設計工具中，按一下所要使用服務的服務安裝程式。  
  
3. 在 [屬性] 視窗中，將 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性設定為下列其中一項：  
  
    |若要安裝服務|設定此值|  
    |----------------------------------|--------------------|  
    |當電腦重新開機時|**自動**|  
    |當明確的使用者動作啟動服務時|**手動**|  
  
    > [!TIP]
    >  若不要讓服務啟動，可以將 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性設定為 **Disabled**。 如果您要將伺服器重新開機多次，而且想要防止要正常啟動的服務被啟動，藉以節省時間，則可以這樣做。  
  
    > [!NOTE]
    >  您可以在安裝服務之後變更這些屬性和其他屬性。  
  
     有數種方式可讓您啟動要將其 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 處理序設定為 **Manual** 的服務：從 [伺服器總管]、從 [Windows 服務控制管理員] 或從程式碼。 請務必注意，並非所有的這些方法都會在**服務控制管理員**的內容中實際啟動服務；**伺服器總管**和以程式設計方式啟動服務的方法會實際操作該控制程式。  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>以手動方式從伺服器總管啟動服務  
  
1. 在 [伺服器總管] 中，加入您所需的伺服器 (如果尚未列出該伺服器)。 如需詳細資訊，請參閱＜如何：存取及初始化伺服器總管/資料庫總管＞。  
  
2. 展開 [服務] 節點，然後找出您想要啟動的服務。  
  
3. 在服務名稱上按一下滑鼠右鍵，然後按一下 [啟動]。  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>以手動方式從服務控制管理員啟動服務  
  
1. 執行下列其中一個動作來開啟 [服務控制管理員]：  
  
    -   在 Windows XP 和 2000 Professional 中，以滑鼠右鍵按一下桌面上的 [我的電腦]，然後按一下 [管理]。 在出現的對話方塊中，展開 [服務與應用程式] 節點。  
  
         \-或-  
  
    -   在 Windows Server 2003 和 Windows 2000 Server 中，按一下 [啟動]、指向 [程式集]、按一下 [系統管理工具]，然後按一下 [服務]。  
  
        > [!NOTE]
        >  在 Windows NT 4.0 版中，您可以從 [控制台] 開啟此對話方塊。  
  
     現在您應該會看到服務列於這個視窗的 [服務] 區段中。  
  
2. 從清單中選取您的服務，以滑鼠右鍵按一下該服務，然後按一下 [啟動]。  
  
### <a name="to-manually-start-a-service-from-code"></a>以手動方式從程式碼啟動服務  
  
1. 建立 <xref:System.ServiceProcess.ServiceController> 類別的執行個體，並將它設定為與您想要管理的服務互動。  
  
2. 呼叫 <xref:System.ServiceProcess.ServiceController.Start%2A> 方法啟動服務。  
  
## <a name="see-also"></a>另請參閱

- [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [作法：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [作法：將安裝程式新增至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
