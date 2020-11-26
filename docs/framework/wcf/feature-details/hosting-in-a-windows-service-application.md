---
title: 在 Windows 服務應用程式中裝載
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: 9f5c78adad34b5fed53a50e85f0361eef469de99
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243068"
---
# <a name="hosting-in-a-windows-service-application"></a>在 Windows 服務應用程式中裝載

Windows 服務 (之前稱為 Windows NT 服務) 所提供的處理序模型特別適合那些必須駐留在長時間執行的可執行檔中，且不會顯示任何使用者介面形式的應用程式使用。 Windows 服務應用程式的處理序存留期是由服務控制管理員 (SCM) 負責管理，可讓您啟動、停止與暫停 Windows 服務應用程式。 您可以將 Windows 服務進程設定為在電腦啟動時自動啟動，使其成為適合「永遠開啟」應用程式的裝載環境。 如需 Windows 服務應用程式的詳細資訊，請參閱 [Windows 服務應用程式](https://go.microsoft.com/fwlink/?LinkId=89450)。  
  
 裝載長時間執行 Windows Communication Foundation (WCF) 服務的應用程式，與 Windows 服務共用許多特性。 尤其是，WCF 服務是長時間執行的伺服器可執行檔，不會直接與使用者互動，因此不會執行任何形式的使用者介面。 因此，在 Windows 服務應用程式中裝載 WCF 服務，是建立強大、長時間執行的 WCF 應用程式的一個選項。  
  
 WCF 開發人員通常必須決定是否要將其 WCF 應用程式裝載于 Windows 服務應用程式內，或是在 Internet Information Services (IIS) 或 Windows Process Activation Service (是) 裝載環境中。 在下列情況中，您應該考慮使用 Windows 服務應用程式：  
  
- 您的應用程式需要明確的啟動。 例如，您的應用程式必須在伺服器啟動時自動啟動，而非為了回應第一個傳入訊息才動態啟動時，您就應該使用 Windows 服務。  
  
- 裝載應用程式的處理序一旦啟動，就必須維持在執行狀態。 一旦啟動，Windows 服務處理序就會維持在執行狀態，除非伺服器管理員透過服務控制管理員明確地加以關閉。 裝載在 IIS 或 WAS 的應用程式可以動態啟動與停止，以便充分運用系統資源。 需要對自身裝載處理序存留期擁有明確掌控權的應用程式，應該使用 Windows 服務，而不要使用 IIS 或 WAS。  
  
- 您的 WCF 服務必須在 Windows Server 2003 上執行，並使用 HTTP 以外的傳輸。 在 Windows Server 2003 上，IIS 6.0 裝載環境僅限於 HTTP 通訊。 Windows 服務應用程式不受限於這種限制，而且可以使用任何傳輸 WCF 支援的，包括 net.tcp、net.pipe 和 net.tcp。  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>若要在 Windows 服務應用程式中裝載 WCF  
  
1. 建立 Windows 服務應用程式。 您可以使用 <xref:System.ServiceProcess> 命名空間中的類別，以 Managed 程式碼來撰寫 Windows 服務應用程式。 此應用程式必須包含一個繼承自 <xref:System.ServiceProcess.ServiceBase> 的類別。  
  
2. 將 WCF 服務的存留期連結至 Windows 服務應用程式的存留期。 一般來說，您想要在裝載服務啟動時，裝載于 Windows 服務應用程式中的 WCF 服務會變成作用中、停止在主控服務停止時接聽訊息，並在 WCF 服務遇到錯誤時關閉裝載進程。 執行下列工作即可達成這點：  
  
    - 覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 以開啟一或多個 <xref:System.ServiceModel.ServiceHost> 執行個體。 單一 Windows 服務應用程式可以裝載多個以群組方式啟動和停止的 WCF 服務。  
  
    - 覆寫 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 以 <xref:System.ServiceModel.Channels.CommunicationObject.Closed> 在執行 <xref:System.ServiceModel.ServiceHost> 期間啟動的任何執行中 WCF 服務上呼叫 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 。  
  
    - 訂閱 <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> 的 <xref:System.ServiceModel.ServiceHost> 事件，並在發生錯誤時，使用 <xref:System.ServiceProcess.ServiceController> 類別來關閉 Windows 服務應用程式。  
  
     裝載 WCF 服務的 windows 服務應用程式的部署和管理方式，與不使用 WCF 的 Windows 服務應用程式相同。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceProcess>
- [逐步解說：在元件設計工具中建立 Windows 服務應用程式](https://go.microsoft.com/fwlink/?LinkId=94875)
- [作法：在受控的 Windows 服務中裝載 WCF 服務](how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Windows 服務主機](../samples/windows-service-host.md)
- [服務應用程式的程式設計架構](https://go.microsoft.com/fwlink/?LinkId=94876)
- [Windows Server AppFabric 裝載功能](/previous-versions/appfabric/ee677189(v=azure.10))
