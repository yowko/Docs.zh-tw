---
title: "在 Windows 服務應用程式中裝載"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 07823da6a920a22e35932f32f9320499d9cc84a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-in-a-windows-service-application"></a>在 Windows 服務應用程式中裝載
Windows 服務 (之前稱為 Windows NT 服務) 所提供的處理序模型特別適合那些必須駐留在長時間執行的可執行檔中，且不會顯示任何使用者介面形式的應用程式使用。 Windows 服務應用程式的處理序存留期是由服務控制管理員 (SCM) 負責管理，可讓您啟動、停止與暫停 Windows 服務應用程式。 您可以設定 Windows 服務處理序啟動時自動啟動電腦，因此適合裝載 「 永遠開啟 」 應用程式的環境。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Windows 服務應用程式，請參閱[Windows 服務應用程式](http://go.microsoft.com/fwlink/?LinkId=89450)。  
  
 裝載長時間執行 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務的應用程式會有許多 Windows 服務的特徵。 值得一提的是，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務這項長時間執行的伺服器可執行檔不會直接與使用者互動，因此不會實作任何形式的使用者介面。 因此，建置穩固、長時間執行的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式時，可以選擇將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務裝載到 Windows 服務應用程式中。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 開發人員經常必須決定是否將其 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式裝載到 Windows 服務應用程式內或是網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 裝載環境中。 在下列情況中，您應該考慮使用 Windows 服務應用程式：  
  
-   您的應用程式需要明確的啟動。 例如，您的應用程式必須在伺服器啟動時自動啟動，而非為了回應第一個傳入訊息才動態啟動時，您就應該使用 Windows 服務。  
  
-   裝載應用程式的處理序一旦啟動，就必須維持在執行狀態。 一旦啟動，Windows 服務處理序就會維持在執行狀態，除非伺服器管理員透過服務控制管理員明確地加以關閉。 裝載在 IIS 或 WAS 的應用程式可以動態啟動與停止，以便充分運用系統資源。 需要對自身裝載處理序存留期擁有明確掌控權的應用程式，應該使用 Windows 服務，而不要使用 IIS 或 WAS。  
  
-   您的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務必須在 Windows Server 2003 上執行，並使用 HTTP 以外的傳輸。 在 Windows Server 2003 上，會將 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 裝載環境限為僅適用 HTTP 通訊。 Windows 服務應用程式不受到這項限制的約束，可以使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所支援的任何傳輸，包括 net.tcp、net.pipe 和 net.msmq。  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>若要在 Windows 服務應用程式中裝載 WCF  
  
1.  建立 Windows 服務應用程式。 您可以使用 <xref:System.ServiceProcess> 命名空間中的類別，以 Managed 程式碼來撰寫 Windows 服務應用程式。 此應用程式必須包含一個繼承自 <xref:System.ServiceProcess.ServiceBase> 的類別。  
  
2.  將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的存留期連接至 Windows 服務應用程式的存留期。 一般來說，您會希望裝載於 Windows 服務應用程式內的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務能夠在裝載服務啟動時變成作用中、當裝載服務停止時隨之停止接聽訊息，並且在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務遭遇錯誤時關閉裝載處理序。 執行下列工作即可達成這點：  
  
    -   覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 以開啟一或多個 <xref:System.ServiceModel.ServiceHost> 執行個體。 單一 Windows 服務應用程式可以裝載多個以群組為單位啟動並停止的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。  
  
    -   覆寫 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 以呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Closed> (位於任何執行中 <xref:System.ServiceModel.ServiceHost> 服務的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，而這些服務都是在執行 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 期間所啟動)。  
  
    -   訂閱 <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> 的 <xref:System.ServiceModel.ServiceHost> 事件，並在發生錯誤時，使用 <xref:System.ServiceProcess.ServiceController> 類別來關閉 Windows 服務應用程式。  
  
     負責裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的 Windows 服務應用程式，其部署與管理方式將與不使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的 Windows 服務應用程式相同。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceProcess>  
 [逐步解說： 在元件設計工具中建立 Windows 服務應用程式](http://go.microsoft.com/fwlink/?LinkId=94875)  
 [如何： 將 WCF 服務裝載於 Managed 的 Windows 服務](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Windows 服務主機](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [服務應用程式的程式設計架構](http://go.microsoft.com/fwlink/?LinkId=94876)  
 [Windows Server App Fabric 裝載功能](http://go.microsoft.com/fwlink/?LinkId=201276)
