---
title: 在 Windows 服務應用程式中裝載
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: b5167e61bd825ce56905149237dae05ebb44b134
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613312"
---
# <a name="hosting-in-a-windows-service-application"></a>在 Windows 服務應用程式中裝載
Windows 服務 (之前稱為 Windows NT 服務) 所提供的處理序模型特別適合那些必須駐留在長時間執行的可執行檔中，且不會顯示任何使用者介面形式的應用程式使用。 Windows 服務應用程式的處理序存留期是由服務控制管理員 (SCM) 負責管理，可讓您啟動、停止與暫停 Windows 服務應用程式。 您可以設定為啟動電腦，因此合適的裝載環境為 「 永遠開啟 」 應用程式時自動啟動 Windows 服務處理程序。 如需有關 Windows 服務應用程式的詳細資訊，請參閱 < [Windows 服務應用程式](https://go.microsoft.com/fwlink/?LinkId=89450)。  
  
 裝載長時間執行的 Windows Communication Foundation (WCF) 服務的應用程式與 Windows 服務共用許多特性。 特別是，WCF 服務是長時間執行伺服器可執行檔不會直接與使用者互動，因此不會實作任何形式的使用者介面。 因此，裝載 Windows 服務應用程式的 WCF 服務是建置穩固、 長時間執行的 WCF 應用程式的其中一個選項。  
  
 通常，WCF 開發人員必須決定是否要裝載 WCF 應用程式到 Windows 服務應用程式，或在 Internet Information Services (IIS) 或 Windows Process Activation Service (WAS) 裝載環境內。 在下列情況中，您應該考慮使用 Windows 服務應用程式：  
  
- 您的應用程式需要明確的啟動。 例如，您的應用程式必須在伺服器啟動時自動啟動，而非為了回應第一個傳入訊息才動態啟動時，您就應該使用 Windows 服務。  
  
- 裝載應用程式的處理序一旦啟動，就必須維持在執行狀態。 一旦啟動，Windows 服務處理序就會維持在執行狀態，除非伺服器管理員透過服務控制管理員明確地加以關閉。 裝載在 IIS 或 WAS 的應用程式可以動態啟動與停止，以便充分運用系統資源。 需要對自身裝載處理序存留期擁有明確掌控權的應用程式，應該使用 Windows 服務，而不要使用 IIS 或 WAS。  
  
- 您的 WCF 服務必須在 Windows Server 2003 上執行，並使用 HTTP 以外的傳輸。 在 Windows Server 2003 上，會將 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 裝載環境限為僅適用 HTTP 通訊。 Windows 服務應用程式不會受限於這項限制，而且可以使用任何傳輸 WCF 支援，包括 net.tcp、 net.pipe 和 net.msmq。  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>若要在 Windows 服務應用程式中裝載 WCF  
  
1. 建立 Windows 服務應用程式。 您可以使用 <xref:System.ServiceProcess> 命名空間中的類別，以 Managed 程式碼來撰寫 Windows 服務應用程式。 此應用程式必須包含一個繼承自 <xref:System.ServiceProcess.ServiceBase> 的類別。  
  
2. 連結的 Windows 服務應用程式存留期的 WCF 服務的存留期間。 一般而言，您會想要成為作用中裝載的服務啟動時，請停止接聽訊息時停止，並關閉裝載處理序，當發生錯誤時的 WCF 服務主控的服務 Windows 服務應用程式中裝載的 WCF 服務。 執行下列工作即可達成這點：  
  
    - 覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 以開啟一或多個 <xref:System.ServiceModel.ServiceHost> 執行個體。 單一的 Windows 服務應用程式可以裝載多個 WCF 服務的啟動和停止做為群組。  
  
    - 覆寫<xref:System.ServiceProcess.ServiceBase.OnStop%2A>來呼叫<xref:System.ServiceModel.Channels.CommunicationObject.Closed>上<xref:System.ServiceModel.ServiceHost>期間所啟動的任何執行 WCF 服務<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>。  
  
    - 訂閱 <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> 的 <xref:System.ServiceModel.ServiceHost> 事件，並在發生錯誤時，使用 <xref:System.ServiceProcess.ServiceController> 類別來關閉 Windows 服務應用程式。  
  
     裝載 WCF 服務的 Windows 服務應用程式部署與管理方式相同，因為不會進行 Windows 服務應用程式使用 WCF。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceProcess>
- [逐步解說：在元件設計工具中建立 Windows 服務應用程式](https://go.microsoft.com/fwlink/?LinkId=94875)
- [如何：將 WCF 服務裝載於 Managed 的 Windows 服務](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Windows 服務主機](../../../../docs/framework/wcf/samples/windows-service-host.md)
- [服務應用程式的程式設計架構](https://go.microsoft.com/fwlink/?LinkId=94876)
- [Windows Server AppFabric 裝載功能](https://go.microsoft.com/fwlink/?LinkId=201276)
