---
title: "服務應用程式的程式設計架構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: e9c16f2e603a3ce9bbc59be4e01aa492239d2c63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="service-application-programming-architecture"></a>服務應用程式的程式設計架構
Windows 服務應用程式為基礎的類別，繼承自<xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>類別。 您覆寫這個類別的方法，並定義它們，以判斷您的服務行為的功能。  
  
 涉及服務建立的的主要類別如下：  
  
-   <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>— 您覆寫方法<xref:System.ServiceProcess.ServiceBase>類別建立服務時，並定義程式碼以判斷如何在此服務函式繼承類別。  
  
-   <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType>和<xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType>— 您可以使用這些類別來安裝和解除安裝您的服務。  
  
 此外，類別命名為<xref:System.ServiceProcess.ServiceController>可用來管理此服務本身。 這個類別並不會涉及建立服務，但可用來啟動及停止服務，傳遞命令，以及傳回一連串的列舉型別。  
  
## <a name="defining-your-services-behavior"></a>定義您的服務行為  
 在服務類別中，您已覆寫基底類別函式，以決定服務控制管理員中變更您的服務狀態時，會發生什麼事。 <xref:System.ServiceProcess.ServiceBase>類別會公開下列方法，您可以覆寫，以將自訂行為。  
  
|方法|若要覆寫|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|表示當服務開始執行時，應該採取什麼動作。 您必須撰寫程式碼，在此程序，為您的服務可以執行實際工作。|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|指出暫停您的服務時要採取的動作。|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|表示當您的服務會停止執行時要採取的動作。|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|表示當您的服務會繼續正常運作，在暫停後要採取的動作。|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|表示之前的系統關機，如果您的服務執行在該時間應該發生。|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|表示當服務收到自訂的命令時要採取的動作。 如需有關自訂命令的詳細資訊，請參閱 MSDN 線上。|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|表示接收電源管理事件，例如電力偏低或暫停的作業時，服務應該如何回應。|  
  
> [!NOTE]
>  這些方法表示服務在其存留期間，通過的狀態服務從某個狀態轉換到下一步。 例如，將永遠不會取得服務回應<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>命令之前，先<xref:System.ServiceProcess.ServiceBase.OnStart%2A>已呼叫。  
  
 有數個其他屬性和感興趣的方法。 這些活動包括：  
  
-   <xref:System.ServiceProcess.ServiceBase.Run%2A>方法<xref:System.ServiceProcess.ServiceBase>類別。 這是服務的主要進入點。 當您建立使用 Windows 服務範本的服務時，程式碼會在您的應用程式中插入`Main`方法來執行服務。 此程式碼看起來像這樣：  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  這些範例會使用型別的陣列<xref:System.ServiceProcess.ServiceBase>所在可以加入您的應用程式包含每個服務，，然後所有的服務可以一起執行。 如果您只會建立單一服務，不過，您可以選擇不使用的陣列，並只宣告新物件繼承自<xref:System.ServiceProcess.ServiceBase>然後加以執行。 如需範例，請參閱[如何： 程式設計方式撰寫服務](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)。  
  
-   一系列的屬性上<xref:System.ServiceProcess.ServiceBase>類別。 這些屬性會決定哪種方法可以呼叫您的服務。 例如，當<xref:System.ServiceProcess.ServiceBase.CanStop%2A>屬性設定為`true`、<xref:System.ServiceProcess.ServiceBase.OnStop%2A>可以呼叫您服務上的方法。 當<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>屬性設定為`true`、<xref:System.ServiceProcess.ServiceBase.OnPause%2A>和<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>可以呼叫的方法。 當您設定這些屬性，以其中一項`true`，您應該覆寫，然後定義處理相關聯的方法。  
  
    > [!NOTE]
    >  您的服務必須至少覆寫<xref:System.ServiceProcess.ServiceBase.OnStart%2A>和<xref:System.ServiceProcess.ServiceBase.OnStop%2A>才能發揮作用。  
  
 您也可以使用名為的元件<xref:System.ServiceProcess.ServiceController>進行通訊，並控制現有服務的行為。  
  
## <a name="see-also"></a>另請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [如何： 建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)
