---
title: System.Web.Routing 整合
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: a80b5c3b336b4fd18b347a25ceaf509baf6461b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184387"
---
# <a name="systemwebrouting-integration"></a>System.Web.Routing 整合
在 Internet 資訊服務 （IIS） 中託管 Windows 通信基礎 （WCF） 服務時，您將一個 .svc 檔放在虛擬目錄中。 此 .svc 檔案會指定要使用的服務主機處理站，以及實作服務的類別。 向服務發出請求時，請在 URI 中指定 .svc 檔，例如`http://contoso.com/EmployeeServce.svc`： 。 對於撰寫 REST 服務的程式設計人員而言，此類型的 URI 不是最佳的方法。 REST 服務的 URI 會指定特定資源，且一般來說沒有任何擴充。 集成<xref:System.Web.Routing>功能允許您託管 WCF REST 服務，該服務無需擴展即可回應 URI。 有關路由的詳細資訊，請參閱[ASP.NET路由](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))。  
  
## <a name="using-systemwebrouting-integration"></a>使用 System.Web.Routing 整合  
 若要使用 <xref:System.Web.Routing> 整合功能，請使用 <xref:System.ServiceModel.Activation.ServiceRoute> 類別建立一個或多個路由，並且將路由加入至 Global.asax 檔案中的 <xref:System.Web.Routing.RouteTable>。 這些路由會指定服務回應的相對 URI。 下列範例示範如何執行。  
  
```aspx-csharp  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));
   }  
</script>  
```  
  
 這會將含有相對 URI 以 Customers 開頭的所有要求路由至 `Service` 服務。  
  
 在 Web.config 檔案中，您必須加入 `System.Web.Routing.UrlRoutingModule` 模組、將 `runAllManagedModulesForAllRequests`屬性設定為 `true`，並且將 `UrlRoutingHandler` 處理常式加入至 `<system.webServer>` 項目，如下列範例所示。  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 這會載入路由需要的模組與處理常式。 如需詳細資訊，請參閱[路由](../../../../docs/framework/wcf/feature-details/routing.md)。 您也必須在 `aspNetCompatibilityEnabled` 項目中，將 `true` 屬性設定為 `<serviceHostingEnvironment>`，如下列範例所示。  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 實作服務的類別必須啟用 ASP.NET 相容性需求，如下列範例所示。  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>另請參閱

- [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [ASP.NET 路由](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))
