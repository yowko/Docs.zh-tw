---
title: 支援的部署案例
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: d0afd12b1c17f9356146aa13c90f8db65ed9ec0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498058"
---
# <a name="supported-deployment-scenarios"></a>支援的部署案例
Windows Communication Foundation (WCF) 支援在部分信任應用程式中使用的功能子集主要被為了符合某些，但不是全部案例使用 WCF 的需求。 在伺服器上，WCF 符合網際網路範圍的要求會共用裝載提供者執行第三方應用程式中[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]因為安全性緣故而度信任權限。 在用戶端，WCF 部分信任支援主要為了符合需求的部署技術例如[ClickOnce 部署](http://go.microsoft.com/fwlink/?LinkId=83712)或[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]的 XAML 瀏覽器應用程式技術，允許順暢且安全部署桌面應用程式，從受信任的網站。  
  
## <a name="minimum-permission-requirements"></a>基本權限需求  
 WCF 在執行下的下列標準具名權限集的應用程式中支援功能的子集：  
  
-   中度信任權限  
  
-   網際網路區域權限  
  
 嘗試在具有更嚴格的權限的部分信任應用程式中使用 WCF，可能會導致在執行階段的安全性例外狀況。  
  
 如需這些使用權限集合所支援之功能的詳細資訊，請參閱 [Partial Trust Feature Compatibility](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)。  
  
## <a name="partial-trust-on-the-server"></a>伺服器的部分信任  
 許多 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 應用程式裝載服務的商業提供者要求，在他們的伺服器上執行的應用程式必須透過 [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] 中度信任使用權限集合來執行。 在這些環境中可以執行 WCF 服務，前提是它們使用<xref:System.ServiceModel.BasicHttpBinding>、 <xref:System.ServiceModel.WebHttpBinding>，或 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> 具有傳輸層級安全性。  
  
 中度信任裝載環境中執行的 WCF 服務可以也做為中介層服務將訊息傳送至用戶端要求的回應中的其他伺服器。 如果裝載的環境已經授與應用程式適當的 <xref:System.Net.WebPermission> 以便對目的伺服器發出傳出要求時，伺服器便會支援中介層案例。  
  
 除了 SOAP 訊息使用其中一種支援的 SOAP 繫結，支援 WCF<xref:System.ServiceModel.WebHttpBinding>來建置 Web 樣式服務，在部分信任應用程式。 [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)， [WCF 新聞訂閱](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)，和[AJAX 整合與 JSON 支援](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)WCF 的功能都支援在部分信任中。  
  
 工作流程服務需要完全信任使用權限，而且無法用在部分信任應用程式中。  
  
 如需詳細資訊，請參閱[How to： 使用 ASP.NET 2.0 中度信任](http://go.microsoft.com/fwlink/?LinkId=84603)。  
  
## <a name="partial-trust-on-the-client"></a>用戶端的部分信任  
 在從不受信任的網際網路網站中下載並執行程式碼時，必須採取特定的安全性預防措施。 [ClickOnce 部署](http://go.microsoft.com/fwlink/?LinkId=83712) (英文) 和 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]的 XAML 瀏覽器應用程式 (XBAP) 技術兩者都會透過部分信任將有限的使用權限 (網際網路區域) 授與不受信任的程式碼。  
  
 WCF 可以用來與從部分信任的應用程式透過其中一種部署的遠端伺服器通訊[ClickOnce 部署](http://go.microsoft.com/fwlink/?LinkId=83712)或 XBAP。 網際網路區域使用權限集合包含<xref:System.Net.WebPermission>的原始主機，以允許這些應用程式與使用任何支援 中描述的 WCF 繫結與其來源伺服器進行[部分信任功能相容性](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md).  
  
## <a name="see-also"></a>另請參閱  
 [程式碼存取安全性](http://go.microsoft.com/fwlink/?LinkId=83717)  
 [Windows Presentation Foundation 瀏覽器裝載的應用程式概觀](http://go.microsoft.com/fwlink/?LinkId=98397)  
 [部分信任](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 [ASP.Net 中度信任](http://go.microsoft.com/fwlink/?LinkId=69328)
