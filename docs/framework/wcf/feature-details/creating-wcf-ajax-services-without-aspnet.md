---
title: 建立不含 ASP.NET 的 WCF AJAX 服務
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: de7e5dc075a821518928514be532ea1940c1ff17
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627123"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="eb578-102">建立不含 ASP.NET 的 WCF AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="eb578-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="eb578-103">Windows Communication Foundation (WCF) AJAX 服務可以存取從任何已啟用 JavaScript 的網頁，而不需要 ASP.NET AJAX。</span><span class="sxs-lookup"><span data-stu-id="eb578-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="eb578-104">本主題描述如何建立這類的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="eb578-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="eb578-105">如需使用 WCF 與 ASP.NET AJAX 的指示，請參閱 <<c0> [ 建立 ASP.NET AJAX 的 WCF 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)。</span><span class="sxs-lookup"><span data-stu-id="eb578-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="eb578-106">有三個部分建立的 WCF AJAX 服務：</span><span class="sxs-lookup"><span data-stu-id="eb578-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="eb578-107">建立可以從瀏覽器存取的 AJAX 端點。</span><span class="sxs-lookup"><span data-stu-id="eb578-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="eb578-108">建立與 AJAX 相容的服務合約。</span><span class="sxs-lookup"><span data-stu-id="eb578-108">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="eb578-109">存取 WCF AJAX 服務。</span><span class="sxs-lookup"><span data-stu-id="eb578-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="eb578-110">建立 AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="eb578-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="eb578-111">若要啟用 WCF 服務中的 AJAX 支援的最基本的方式是使用<xref:System.ServiceModel.Activation.WebServiceHostFactory>相關聯的服務，如下列範例所示的.svc 檔案中。</span><span class="sxs-lookup"><span data-stu-id="eb578-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="eb578-112">或者，您也可以使用組態來新增 AJAX 端點。</span><span class="sxs-lookup"><span data-stu-id="eb578-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="eb578-113">在服務端點上使用 <xref:System.ServiceModel.WebHttpBinding>，並使用 <xref:System.ServiceModel.Description.WebHttpBehavior> 設定該端點，如下列程式碼片段中所示。</span><span class="sxs-lookup"><span data-stu-id="eb578-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint   
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="eb578-114">如需實用範例，請參閱 <<c0> [ 含 JSON 和 XML 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb578-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="eb578-115">建立與 AJAX 相容的服務合約</span><span class="sxs-lookup"><span data-stu-id="eb578-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="eb578-116">根據預設，在 AJAX 端點上公開的服務合約會以 XML 格式傳回資料。</span><span class="sxs-lookup"><span data-stu-id="eb578-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="eb578-117">另外，根據預設，服務作業可透過 HTTP POST 對 URL 的要求來存取，這些 URL 包含端點位址，後面接著作業名稱，如下列範例中所示。</span><span class="sxs-lookup"><span data-stu-id="eb578-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="eb578-118">這項作業是使用 HTTP POST 到可存取`http://serviceaddress/endpointaddress/GetCities`並傳回 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="eb578-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="eb578-119">您可以使用完整的 Web 程式設計模型來自訂這些基本面。</span><span class="sxs-lookup"><span data-stu-id="eb578-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="eb578-120">例如，您可以使用 <xref:System.ServiceModel.Web.WebGetAttribute> 或 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性來控制作業回應的 HTTP 動詞命令，或使用這些個別屬性的 `UriTemplate` 屬性來指定自訂 URI。</span><span class="sxs-lookup"><span data-stu-id="eb578-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="eb578-121">如需詳細資訊，請參閱 < [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)主題。</span><span class="sxs-lookup"><span data-stu-id="eb578-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="eb578-122">JSON 資料格式經常用於 AJAX 服務中。</span><span class="sxs-lookup"><span data-stu-id="eb578-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="eb578-123">若要建立傳回 JSON 而非 XML 的作業，請將 <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (或 <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) 屬性設定為 <xref:System.ServiceModel.Web.WebMessageFormat.Json>。</span><span class="sxs-lookup"><span data-stu-id="eb578-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="eb578-124">[獨立 JSON 序列化](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)主題說明如何內建.NET 型別和資料合約型別對應至 JSON。</span><span class="sxs-lookup"><span data-stu-id="eb578-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="eb578-125">一般來說，JSON 要求與回應只會包含一個項目。</span><span class="sxs-lookup"><span data-stu-id="eb578-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="eb578-126">對於前述 `GetCities` 作業，要求類似下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="eb578-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```  
"na"  
```  
  
 <span data-ttu-id="eb578-127">該要求的回應類似下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="eb578-127">The response to that request resembles the following statement.</span></span>  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="eb578-128">如果作業採用額外的參數，要求樣式必須是 wrapped，以將兩個參數同時包裝在單一 JSON 物件中。</span><span class="sxs-lookup"><span data-stu-id="eb578-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="eb578-129">下列範例中是這種樣式 JSON 訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="eb578-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="eb578-130">下列合約接受這個訊息。</span><span class="sxs-lookup"><span data-stu-id="eb578-130">The following contract accepts this message.</span></span>  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="eb578-131">存取 AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="eb578-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="eb578-132">WCF AJAX 端點永遠接受 JSON 和 XML 要求。</span><span class="sxs-lookup"><span data-stu-id="eb578-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="eb578-133">內容類型為"application/json"的 HTTP POST 要求會被視為 JSON，並具有指出 XML (比方說，「 text/xml 」) 的內容類型會被視為 XML。</span><span class="sxs-lookup"><span data-stu-id="eb578-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="eb578-134">HTTP GET 要求會在 URL 本身包含所有要求參數。</span><span class="sxs-lookup"><span data-stu-id="eb578-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="eb578-135">至於如何建立對端點的 HTTP 要求，將留給使用者來決定。</span><span class="sxs-lookup"><span data-stu-id="eb578-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="eb578-136">同時，使用者對於建構可形成要求本體的 JSON 具有完整的掌控權。</span><span class="sxs-lookup"><span data-stu-id="eb578-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="eb578-137">如需從 JavaScript 建立要求的範例，請參閱 <<c0> [ 含 JSON 和 XML 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="eb578-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
