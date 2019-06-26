---
title: 在 Windows Process Activation Service 中裝載
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
ms.openlocfilehash: eeac535eac95b19889d0d8d74115bcddc3a15224
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402344"
---
# <a name="hosting-in-windows-process-activation-service"></a>在 Windows Process Activation Service 中裝載
Windows Process Activation Service (WAS) 管理啟動和包含該主機的 Windows Communication Foundation (WCF) 服務的應用程式的工作者處理序的存留期。 WAS 處理序模型會將 HTTP 伺服器的 IIS 6.0 處理序模型一般化藉由移除 HTTP 的相依性。 這可讓 WCF 服務使用 HTTP 和非 HTTP 通訊協定，例如 Net.TCP，請在裝載環境中支援訊息型啟用，並可讓您裝載大量應用程式，在指定電腦上。  
  
 如在 WAS 裝載環境中，執行建置 WCF 服務的詳細資訊，請參閱[How to:將 WCF 服務裝載於 WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)。  
  
 WAS 處理序模型提供的幾項功能，可將應用程式裝載得更為穩固、容易管理，而且能夠更有效率地運用資源：  
  
- 訊息式的應用程式啟動和背景工作處理序應用程式會動態啟動與停止，以回應透過 HTTP 和非 HTTP 網路通訊協定抵達的傳入工作項目。  
  
- 穩固的應用程式與背景工作處理序回收作業可維護執行中的應用程式健康狀況。  
  
- 集中式應用程式組態和管理。  
  
- 可讓應用程式善用 IIS 處理序模型的優勢，而不需要部署完整的 IIS 安裝項目。  
  
 如需 WAS 功能的詳細資訊，請參閱[IIS 7.0 Beta:IIS 7.0 的 Web 系統管理](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)。  
  
 [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496)搭配[!INCLUDE[iisver](../../../../includes/iisver-md.md)]和 Windows Process Activation Service (WAS) 來提供豐富的應用程式裝載環境，為 NET4 WCF 和 WF 服務。 這些優點包括處理序生命週期管理、處理序回收、共用裝載、快速失敗保護、處理序損壞、隨選啟動和健康監視。 如需詳細資訊，請參閱 < [AppFabric 主控功能](https://go.microsoft.com/fwlink/?LinkId=196494)並[AppFabric 主控概念](https://go.microsoft.com/fwlink/?LinkId=196495)。  
  
## <a name="elements-of-the-was-addressing-model"></a>WAS 定址模型項目  
 包含統一資源識別元 (URI) 位址的應用程式，這些程式碼單元會經由伺服器來管理自身的存留期和執行環境。 單一 WAS 伺服器執行個體可以裝載許多不同的應用程式。 伺服器會組織成群組呼叫的應用程式*站台*。 同一個網站中的應用程式會依階層架構順序加以排列，以反映做為應用程式外部位址使用的 URI 結構。  
  
 應用程式位址包含兩個部分：基底 URI 前置詞和應用程式專屬的相對位址 (路徑)，兩者混合使用時，可以提供應用程式的外部位址。 基底 URI 前置詞是根據網站繫結所建構，並且用於該網站中的所有應用程式。 然後應用程式專屬的路徑片段建構應用程式位址 (例如，"/ /applicationone") 並將它們附加至基底 URI 前置詞 (例如"net.tcp: //localhost") 以完整的應用程式 URI。  
  
 下表針對 WAS 網站 (包含 HTTP 和非 HTTP 網站繫結) 說明幾個可能的定址案例。  
  
|情節|網站繫結|應用程式路徑|基底應用程式 URI|  
|--------------|-------------------|----------------------|---------------------------|  
|僅限 HTTP|http: *: 80:\*|/appTwo|http://localhost/appTwo/|  
|HTTP 和非 HTTP 兩者|http: *: 80:\*<br /><br /> net.tcp:808:\*|/appTwo|http://localhost/appTwo/<br />net.tcp://localhost/appTwo/|  
|僅限非 HTTP|net.pipe: *|/appThree|net.pipe://appThree/|  
  
 您也可以針對應用程式中的服務與資源加以定址。 在應用程式中，應用程式資源會以相對於基底應用程式路徑的方式定址。 例如，假定電腦名稱 contoso.com 上的某個網站同時包含 HTTP 和 Net.TCP 通訊協定的網站繫結。 同時假定該網站包含一個位於 /Billing 的應用程式，以便在 GetOrders.svc 公開服務。 這時，如果 GetOrders.svc 服務公開了包含 SecureEndpoint 相對位址的端點，則服務端點會在下列兩個 URL 中公開：  
  
- `http://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
- `net.tcp://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
  
## <a name="the-was-runtime"></a>WAS 執行階段  
 為了定址與管理方便，應用程式會組織成網站。 在執行階段，應用程式也會組織成應用程式集區中的群組。 一個應用程式集區可包含來自許多不同網站的不同應用程式。 應用程式集區中的所有應用程式都共用一組執行階段特徵。 例如，它們會在相同版本的 Common Language Runtime (CLR) 中執行，而且共用相同的處理序身分識別。 每個應用程式集區都對應至一個背景工作處理序 (w3wp.exe) 的執行個體。 每個在共用應用程式集區內執行的 Managed 應用程式都會透過 CLR AppDomain 與其他應用程式隔離開來。  
  
## <a name="see-also"></a>另請參閱

- [WAS 啟用架構](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [設定用於 WCF 的 WAS](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [如何：安裝及設定 WCF 啟用元件](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [如何：裝載在 WAS 中的 WCF 服務](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)
- [Windows Server AppFabric 裝載功能](https://go.microsoft.com/fwlink/?LinkId=201276)
