---
title: 在 Windows Process Activation Service 中裝載
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
ms.openlocfilehash: 1882feee4e8071f1d32fb59ab02519c6e6fe2684
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143559"
---
# <a name="hosting-in-windows-process-activation-service"></a>在 Windows Process Activation Service 中裝載
當工作者處理序包含裝載 Windows Communication Foundation (WCF) 服務的應用程式時，Windows 處理序啟用服務 (WAS) 會管理這些工作者處理序的啟用和存留期。 WAS 處理序模型會透過移除對 HTTP 的相依性，將 HTTP 伺服器的 IIS 6.0 處理序模型一般化。 這可讓 WCF 服務在支援以訊息為基礎之啟用的主控環境中，同時使用 HTTP 和非 HTTP 通訊協定（例如 Net.tcp），並提供在指定的電腦上裝載大量應用程式的功能。  
  
 如需建立在 WAS 裝載環境中執行之 WCF 服務的詳細資訊，請參閱[如何：在 was 中裝載 Wcf 服務](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)。  
  
 WAS 處理序模型提供的幾項功能，可將應用程式裝載得更為穩固、容易管理，而且能夠更有效率地運用資源：  
  
- 訊息式的應用程式啟動和背景工作處理序應用程式會動態啟動與停止，以回應透過 HTTP 和非 HTTP 網路通訊協定抵達的傳入工作項目。  
  
- 穩固的應用程式與背景工作處理序回收作業可維護執行中的應用程式健康狀況。  
  
- 集中式應用程式組態和管理。  
  
- 可讓應用程式善用 IIS 處理序模型的優勢，而不需要部署完整的 IIS 安裝項目。  
[Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10))適用于 IIS 7.0 和 Windows 進程啟用服務（WAS），以提供豐富的應用程式裝載環境來 NET4 WCF 和 WF 服務。 這些優點包括處理序生命週期管理、處理序回收、共用裝載、快速失敗保護、處理序損壞、隨選啟動和健康監視。 如需詳細資訊，請參閱[Appfabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))和[appfabric 裝載概念](https://docs.microsoft.com/previous-versions/appfabric/ee677371(v=azure.10))。  
  
## <a name="elements-of-the-was-addressing-model"></a>WAS 定址模型項目  
 包含統一資源識別元 (URI) 位址的應用程式，這些程式碼單元會經由伺服器來管理自身的存留期和執行環境。 單一 WAS 伺服器執行個體可以裝載許多不同的應用程式。 伺服器會將應用程式組織成稱為「*網站*」的群組。 同一個網站中的應用程式會依階層架構順序加以排列，以反映做為應用程式外部位址使用的 URI 結構。  
  
 應用程式位址包含兩個部分：基底 URI 前置詞和應用程式專屬的相對位址 (路徑)，兩者混合使用時，可以提供應用程式的外部位址。 基底 URI 前置詞是根據網站繫結所建構，並且用於該網站中的所有應用程式。 接著會藉由取得應用程式特定的路徑片段（例如 "/applicationOne"），並將它們附加至基底 URI 前置詞（例如 "net.tcp：//localhost"）來建立應用程式位址，以抵達完整的應用程式 URI。  
  
 下表針對 WAS 網站 (包含 HTTP 和非 HTTP 網站繫結) 說明幾個可能的定址案例。  
  
|案例|網站繫結|應用程式路徑|基底應用程式 URI|  
|--------------|-------------------|----------------------|---------------------------|  
|僅限 HTTP|HTTP： *：80：\*|/appTwo|`http://localhost/appTwo/`|  
|HTTP 和非 HTTP 兩者|HTTP： *：80：\*<br /><br /> net.tcp：808：\*|/appTwo|`http://localhost/appTwo/`<br />`net.tcp://localhost/appTwo/`|  
|僅限非 HTTP|net.pipe: *|/appThree|`net.pipe://appThree/`|  
  
 您也可以針對應用程式中的服務與資源加以定址。 在應用程式中，應用程式資源會以相對於基底應用程式路徑的方式定址。 例如，假定電腦名稱 contoso.com 上的某個網站同時包含 HTTP 和 Net.TCP 通訊協定的網站繫結。 同時假定該網站包含一個位於 /Billing 的應用程式，以便在 GetOrders.svc 公開服務。 這時，如果 GetOrders.svc 服務公開了包含 SecureEndpoint 相對位址的端點，則服務端點會在下列兩個 URL 中公開：  
  
- `http://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
- `net.tcp://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
  
## <a name="the-was-runtime"></a>WAS 執行階段  
 為了定址與管理方便，應用程式會組織成網站。 在執行階段，應用程式也會組織成應用程式集區中的群組。 一個應用程式集區可包含來自許多不同網站的不同應用程式。 應用程式集區中的所有應用程式都共用一組執行階段特徵。 例如，它們會在相同版本的 Common Language Runtime (CLR) 中執行，而且共用相同的處理序身分識別。 每個應用程式集區都對應至一個背景工作處理序 (w3wp.exe) 的執行個體。 每個在共用應用程式集區內執行的 Managed 應用程式都會透過 CLR AppDomain 與其他應用程式隔離開來。  
  
## <a name="see-also"></a>另請參閱

- [WAS 啟動架構](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [設定用於 WCF 的 WAS](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [如何：安裝和設定 WCF 啟用元件](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)
- [Windows Server AppFabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
