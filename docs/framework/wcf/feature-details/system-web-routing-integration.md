---
title: System.Web.Routing 整合
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c3a5b9965f63a9fc501025493b3a323013ea2a4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="a6594-102">System.Web.Routing 整合</span><span class="sxs-lookup"><span data-stu-id="a6594-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="a6594-103">在 Internet Information Service (IIS) 中裝載 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務時，您會將一個 .svc 檔案置入虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="a6594-103">When hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="a6594-104">此 .svc 檔案會指定要使用的服務主機處理站，以及實作服務的類別。</span><span class="sxs-lookup"><span data-stu-id="a6594-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="a6594-105">時，對服務提出要求的.svc 檔案中指定 URI，例如： http://contoso.com/EmployeeServce.svc。</span><span class="sxs-lookup"><span data-stu-id="a6594-105">When making requests to the service you specify the .svc file in the URI, for example: http://contoso.com/EmployeeServce.svc.</span></span> <span data-ttu-id="a6594-106">對於撰寫 REST 服務的程式設計人員而言，此類型的 URI 不是最佳的方法。</span><span class="sxs-lookup"><span data-stu-id="a6594-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="a6594-107">REST 服務的 URI 會指定特定資源，且一般來說沒有任何擴充。</span><span class="sxs-lookup"><span data-stu-id="a6594-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="a6594-108"><xref:System.Web.Routing> 整合功能可讓您裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST 服務，該服務不需要擴充即可回應 URI。</span><span class="sxs-lookup"><span data-stu-id="a6594-108">The <xref:System.Web.Routing> integration feature allows you to host a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST service that responds to URIs without an extension.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a6594-109"> 路由，請參閱[ASP.NET 路由](http://go.microsoft.com/fwlink/?LinkId=184660)和[AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md)範例。</span><span class="sxs-lookup"><span data-stu-id="a6594-109"> routing see [ASP.NET Routing](http://go.microsoft.com/fwlink/?LinkId=184660) and the [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) sample.</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="a6594-110">使用 System.Web.Routing 整合</span><span class="sxs-lookup"><span data-stu-id="a6594-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="a6594-111">若要使用 <xref:System.Web.Routing> 整合功能，請使用 <xref:System.ServiceModel.Activation.ServiceRoute> 類別建立一個或多個路由，並且將路由加入至 Global.asax 檔案中的 <xref:System.Web.Routing.RouteTable>。</span><span class="sxs-lookup"><span data-stu-id="a6594-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="a6594-112">這些路由會指定服務回應的相對 URI。</span><span class="sxs-lookup"><span data-stu-id="a6594-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="a6594-113">下列範例顯示如何執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="a6594-113">The following example shows how to do this.</span></span>  
  
```  
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
  
 <span data-ttu-id="a6594-114">這會將含有相對 URI 以 Customers 開頭的所有要求路由至 `Service` 服務。</span><span class="sxs-lookup"><span data-stu-id="a6594-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="a6594-115">在 Web.config 檔案中，您必須加入 `System.Web.Routing.UrlRoutingModule` 模組、將 `runAllManagedModulesForAllRequests`屬性設定為 `true`，並且將 `UrlRoutingHandler` 處理常式加入至 `<system.webServer>` 項目，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a6594-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a6594-116">這會載入路由需要的模組與處理常式。</span><span class="sxs-lookup"><span data-stu-id="a6594-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="a6594-117">如需詳細資訊，請參閱[路由](../../../../docs/framework/wcf/feature-details/routing.md)。</span><span class="sxs-lookup"><span data-stu-id="a6594-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="a6594-118">您也必須在 `aspNetCompatibilityEnabled` 項目中，將 `true` 屬性設定為 `<serviceHostingEnvironment>`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a6594-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="a6594-119">實作服務的類別必須啟用 ASP.NET 相容性需求，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a6594-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6594-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6594-120">See Also</span></span>  
 [<span data-ttu-id="a6594-121">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="a6594-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="a6594-122">ASP.NET 路由</span><span class="sxs-lookup"><span data-stu-id="a6594-122">ASP.NET Routing</span></span>](http://go.microsoft.com/fwlink/?LinkId=184660)
