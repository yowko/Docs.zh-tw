---
title: HOW TO：不使用組態新增 ASP.NET AJAX 端點
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d82febd776bfc51e3e9725701253ed19996349b5
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="0928d-102">HOW TO：不使用組態新增 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="0928d-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="0928d-103"> 可讓您建立服務以公開啟用 ASP.NET AJAX 的端點，並可在用戶端網站上透過 JavaScript 來呼叫此端點。</span><span class="sxs-lookup"><span data-stu-id="0928d-103"> allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="0928d-104">若要建立此類端點，您可以使用組態檔 (與建立其他所有 WCF 端點一樣)，或是使用不需要任何組態項目的方法。</span><span class="sxs-lookup"><span data-stu-id="0928d-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="0928d-105">本主題示範第二種方法。</span><span class="sxs-lookup"><span data-stu-id="0928d-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="0928d-106">若要以不包含組態的 ASP.NET AJAX 端點來建立服務，服務必須由網際網路資訊服務 (IIS) 加以裝載。</span><span class="sxs-lookup"><span data-stu-id="0928d-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="0928d-107">若要啟用 ASP.NET AJAX 端點，使用這種方式，指定<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>中 Factory 參數[ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) .svc 檔案中的指示詞。</span><span class="sxs-lookup"><span data-stu-id="0928d-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="0928d-108">這項自訂的處理站元件會自動設定 ASP.NET AJAX 端點，以便用戶端網站上的 JavaScript 能夠對它呼叫。</span><span class="sxs-lookup"><span data-stu-id="0928d-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="0928d-109">如需實用範例，請參閱[AJAX 服務沒有設定](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="0928d-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="0928d-110">如何設定使用組態項目為 ASP.NET AJAX 端點的大綱，請參閱[How to： 使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="0928d-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="0928d-111">若要建立基本 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="0928d-111">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="0928d-112">使用以 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 屬性標記的介面來定義基本的 <xref:System.ServiceModel.ServiceContractAttribute> 服務合約。</span><span class="sxs-lookup"><span data-stu-id="0928d-112">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="0928d-113">以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。</span><span class="sxs-lookup"><span data-stu-id="0928d-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="0928d-114">請務必設定 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="0928d-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="0928d-115">使用 `ICalculator` 來實作 `CalculatorService` 服務合約。</span><span class="sxs-lookup"><span data-stu-id="0928d-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="0928d-116">定義 `ICalculator` 和 `CalculatorService` 實作的命名空間，方法是將它們包裝在命名空間區塊中。</span><span class="sxs-lookup"><span data-stu-id="0928d-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="0928d-117">若要將服務裝載到不含組態的網際網路資訊服務中</span><span class="sxs-lookup"><span data-stu-id="0928d-117">To host the service in Internet Information Services without configuration</span></span>  
  
1.  <span data-ttu-id="0928d-118">在應用程式中建立名為 service 且包含 .svc 副檔名的新檔案。</span><span class="sxs-lookup"><span data-stu-id="0928d-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="0928d-119">藉由新增適當的編輯此檔案[ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞服務的資訊。</span><span class="sxs-lookup"><span data-stu-id="0928d-119">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="0928d-120">指定<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>到用於在[ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞，以自動設定 ASP.NET AJAX 端點。</span><span class="sxs-lookup"><span data-stu-id="0928d-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  <span data-ttu-id="0928d-121">建置服務並從用戶端呼叫。</span><span class="sxs-lookup"><span data-stu-id="0928d-121">Build the service and call it from the client.</span></span> <span data-ttu-id="0928d-122">網際網路資訊服務 (IIS) 會在收到呼叫時啟用服務。</span><span class="sxs-lookup"><span data-stu-id="0928d-122">Internet Information Services (IIS) activates the service when called.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="0928d-123"> 裝載在 IIS 中，請參閱[How to： 將 WCF 服務裝載於 IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="0928d-123"> hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="0928d-124">若要呼叫服務</span><span class="sxs-lookup"><span data-stu-id="0928d-124">To call the service</span></span>  
  
1.  <span data-ttu-id="0928d-125">端點會設定在與.svc 檔，相對的空白位址，因此服務現在可以使用而且可以將要求傳送至 service.svc / 叫用\<作業 >-例如，service.svc/add`Add`作業。</span><span class="sxs-lookup"><span data-stu-id="0928d-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="0928d-126">您可以將服務 URL 輸入 ASP.NET AJAX 指令碼管理員控制項的指令碼集合來加以使用。</span><span class="sxs-lookup"><span data-stu-id="0928d-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="0928d-127">如需範例，請參閱[AJAX 服務沒有設定](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="0928d-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0928d-128">範例</span><span class="sxs-lookup"><span data-stu-id="0928d-128">Example</span></span>  
  
 <span data-ttu-id="0928d-129">自動設定的端點會在相對於基底 URL 的空白位址建立。</span><span class="sxs-lookup"><span data-stu-id="0928d-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="0928d-130">您也可以新增組態檔並搭配這個方法使用。</span><span class="sxs-lookup"><span data-stu-id="0928d-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="0928d-131">如果組態檔包含端點定義，則這些端點就會新增到自動設定的端點中。</span><span class="sxs-lookup"><span data-stu-id="0928d-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="0928d-132">例如，service.svc 會使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 而服務目錄則包含了 Web.config 檔案，以便透過 "soap" 相對位址上的 <xref:System.ServiceModel.BasicHttpBinding> 來定義相同服務的端點。</span><span class="sxs-lookup"><span data-stu-id="0928d-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="0928d-133">在此情況中，服務包含了兩個端點：一個位於 service.svc (回應 ASP.NET AJAX 的要求) 而另一個則位於 service.svc/soap (回應 SOAP 的要求)。</span><span class="sxs-lookup"><span data-stu-id="0928d-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="0928d-134">如果組態檔在空白的相對位址上定義了端點，並且使用了 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>，則會擲回例外狀況，而且服務也將無法啟動。</span><span class="sxs-lookup"><span data-stu-id="0928d-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="0928d-135">您無法在自動設定的端點上使用組態來修改設定。</span><span class="sxs-lookup"><span data-stu-id="0928d-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="0928d-136">如果必須修改任何設定 (例如，讀取器配額)，您不可以藉由移除 .svc 檔案中的 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 並為端點建立組態項目的方式來使用無組態檔的方式。</span><span class="sxs-lookup"><span data-stu-id="0928d-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="0928d-137">如果您的服務要求使用 ASP.NET 相容性模式 (例如，如果它使用 <xref:System.Web.HttpContext> 類別或 ASP.NET 授權機制) 則您還是需要組態檔來開啟此模式。</span><span class="sxs-lookup"><span data-stu-id="0928d-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="0928d-138">所需的組態項目是[ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)元素，其必須以下列方式加入。</span><span class="sxs-lookup"><span data-stu-id="0928d-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="0928d-139">如需詳細資訊，請參閱[WCF 服務與 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)主題。</span><span class="sxs-lookup"><span data-stu-id="0928d-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="0928d-140"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 類別是 <xref:System.ServiceModel.Activation.ServiceHostFactory> 的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="0928d-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="0928d-141">服務主機 factory 機制的詳細說明，請參閱[擴充裝載使用 ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)主題。</span><span class="sxs-lookup"><span data-stu-id="0928d-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0928d-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0928d-142">See Also</span></span>  
 [<span data-ttu-id="0928d-143">建立 ASP.NET AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="0928d-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="0928d-144">如何：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="0928d-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
