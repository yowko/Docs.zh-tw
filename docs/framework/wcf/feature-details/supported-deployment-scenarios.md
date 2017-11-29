---
title: "支援的部署案例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22dcace51b2c73193356450b4b210d1c1a899e28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="supported-deployment-scenarios"></a>支援的部署案例
在部分信任應用程式中，支援使用的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 功能子集主要是為了符合某些 (但非全部) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]案例的使用需求。 在伺服器上， [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 需符合網際網路範圍的共用裝載提供者需求，因為這些提供者會因為安全性緣故而透過 [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] 中度信任權限來執行協力廠商應用程式。 在用戶端上， [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 部分信任支援主要是為了符合 [ClickOnce 部署](http://go.microsoft.com/fwlink/?LinkId=83712) (英文) 或 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]的 XAML 瀏覽器應用程式技術之類的部署技術需求，以便從不受信任的網站進行無接縫且安全的桌面應用程式部署作業。  
  
## <a name="minimum-permission-requirements"></a>基本權限需求  
 對於在下列標準具名權限集合中執行的應用程式，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援其中的功能子集：  
  
-   中度信任權限  
  
-   網際網路區域權限  
  
 嘗試在部分信任且包含更多限制性權限的應用程式中使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可能會在執行階段導致安全性例外狀況。  
  
 如需這些使用權限集合所支援之功能的詳細資訊，請參閱 [Partial Trust Feature Compatibility](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)。  
  
## <a name="partial-trust-on-the-server"></a>伺服器的部分信任  
 許多 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 應用程式裝載服務的商業提供者要求，在他們的伺服器上執行的應用程式必須透過 [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] 中度信任使用權限集合來執行。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務可以執行在這些環境中，前提是它們使用<xref:System.ServiceModel.BasicHttpBinding>、 <xref:System.ServiceModel.WebHttpBinding>，或 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> 具有傳輸層級安全性。  
  
 在中度信任裝載環境中執行的[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，同樣可以中介層服務的身分將訊息傳送至其他服務以回應用戶端要求。 如果裝載的環境已經授與應用程式適當的 <xref:System.Net.WebPermission> 以便對目的伺服器發出傳出要求時，伺服器便會支援中介層案例。  
  
 除了 SOAP 訊息 (使用其中一項支援的 SOAP 繫結) 之外， [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 還支援 <xref:System.ServiceModel.WebHttpBinding> ，以便在部分信任應用程式中建置 Web 樣式的服務。 [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)， [WCF 新聞訂閱](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)，和[AJAX 整合與 JSON 支援](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)功能[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]都是在部分信任中支援。  
  
 工作流程服務需要完全信任使用權限，而且無法用在部分信任應用程式中。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [HOW TO：在 ASP.NET 2.0 使用中度信任](http://go.microsoft.com/fwlink/?LinkId=84603)案例的使用需求。  
  
## <a name="partial-trust-on-the-client"></a>用戶端的部分信任  
 在從不受信任的網際網路網站中下載並執行程式碼時，必須採取特定的安全性預防措施。 [ClickOnce 部署](http://go.microsoft.com/fwlink/?LinkId=83712) (英文) 和 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]的 XAML 瀏覽器應用程式 (XBAP) 技術兩者都會透過部分信任將有限的使用權限 (網際網路區域) 授與不受信任的程式碼。  
  
 您可以使用[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 與來自部分信任應用程式 (由 [ClickOnce 部署](http://go.microsoft.com/fwlink/?LinkId=83712) (英文) 或 XBAP 所部署) 的遠端伺服器通訊。 網際網路區域使用權限集合包含來源主機的 <xref:System.Net.WebPermission> ，以允許這些應用程式使用任何一種支援的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結與其來源伺服器進行通訊，這些繫結詳述於 [Partial Trust Feature Compatibility](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)案例的使用需求。  
  
## <a name="see-also"></a>另請參閱  
 [程式碼存取安全性](http://go.microsoft.com/fwlink/?LinkId=83717)  
 [Windows Presentation Foundation 瀏覽器裝載的應用程式概觀](http://go.microsoft.com/fwlink/?LinkId=98397)  
 [部分信任](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 [ASP.Net 中度信任](http://go.microsoft.com/fwlink/?LinkId=69328)
