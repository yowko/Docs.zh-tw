---
title: 含 JSON 和 XML 的 AJAX 服務範例
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f1a3f2185743be6d6331db4aa253a0767484b32d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="48a2e-102">含 JSON 和 XML 的 AJAX 服務範例</span><span class="sxs-lookup"><span data-stu-id="48a2e-102">AJAX Service with JSON and XML Sample</span></span>
<span data-ttu-id="48a2e-103">這個範例會示範如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 建立會傳回 JavaScript 物件標記法 (JSON) 或 XML 資料的 Asynchronous JavaScript 與 XML (AJAX) 服務。</span><span class="sxs-lookup"><span data-stu-id="48a2e-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="48a2e-104">您可以從 Web 瀏覽器用戶端使用 JavaScript 程式碼存取 AJAX 服務。</span><span class="sxs-lookup"><span data-stu-id="48a2e-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="48a2e-105">這個範例是根據[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例。</span><span class="sxs-lookup"><span data-stu-id="48a2e-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="48a2e-106">不像其他 AJAX 範例，這個範例不會使用 ASP.NET AJAX 以及 <xref:System.Web.UI.ScriptManager> 控制項。</span><span class="sxs-lookup"><span data-stu-id="48a2e-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="48a2e-107">搭配一些額外組態時，便可透過 JavaScript 從任何 HTML 網頁存取 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX 服務，以下即顯示此案例。</span><span class="sxs-lookup"><span data-stu-id="48a2e-107">With some additional configuration, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="48a2e-108">如需使用[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]與 ASP.NET AJAX，請參閱[AJAX 範例](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)。</span><span class="sxs-lookup"><span data-stu-id="48a2e-108">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
 <span data-ttu-id="48a2e-109">這個範例會示範如何從 JSON 和 XML 之間切換作業的回應型別。</span><span class="sxs-lookup"><span data-stu-id="48a2e-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="48a2e-110">不論是設定由 ASP.NET AJAX 或 HTML/JavaScript 用戶端頁面存取此服務，這項功能都會提供使用。</span><span class="sxs-lookup"><span data-stu-id="48a2e-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48a2e-111">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="48a2e-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="48a2e-112">若要啟用非 ASP.NET AJAX 用戶端，請使用 .svc 檔案中的 <xref:System.ServiceModel.Activation.WebServiceHostFactory> (而非 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>)。</span><span class="sxs-lookup"><span data-stu-id="48a2e-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="48a2e-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> 會將 <xref:System.ServiceModel.Description.WebHttpEndpoint> 標準端點加入至服務。</span><span class="sxs-lookup"><span data-stu-id="48a2e-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="48a2e-114">在與.svc 檔; 相對的空位址設定端點這表示服務的位址是http://localhost/ServiceModelSamples/service.svc，與作業名稱以外的任何其他後置字元。</span><span class="sxs-lookup"><span data-stu-id="48a2e-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is http://localhost/ServiceModelSamples/service.svc, with no additional suffixes other than the operation name.</span></span>  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 <span data-ttu-id="48a2e-115">Web.config 中的以下區段可用來針對端點進行其他組態變更。</span><span class="sxs-lookup"><span data-stu-id="48a2e-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="48a2e-116">如果不需要額外的變更，也可以加以移除。</span><span class="sxs-lookup"><span data-stu-id="48a2e-116">It can be removed if no extra changes are needed.</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="48a2e-117">預設資料格式<xref:System.ServiceModel.Description.WebHttpEndpoint>為 XML，而預設資料格式<xref:System.ServiceModel.Description.WebScriptEndpoint>為 JSON。</span><span class="sxs-lookup"><span data-stu-id="48a2e-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="48a2e-118">如需詳細資訊，請參閱[不含 ASP.NET 建立 WCF AJAX 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)。</span><span class="sxs-lookup"><span data-stu-id="48a2e-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>  
  
 <span data-ttu-id="48a2e-119">下列範例中的服務是包含兩種作業的標準 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="48a2e-119">The service in the following sample is a standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with two operations.</span></span> <span data-ttu-id="48a2e-120">這兩種作業的 <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> 或 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性上都必須是 <xref:System.ServiceModel.Web.WebInvokeAttribute> 本文樣式，這是 `webHttp` 行為的特定需求，而且不會影響 JSON/XML 資料格式切換。</span><span class="sxs-lookup"><span data-stu-id="48a2e-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 <span data-ttu-id="48a2e-121">指定作業的回應格式為 XML，這是預設設定[ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)行為。</span><span class="sxs-lookup"><span data-stu-id="48a2e-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="48a2e-122">然而，明確指定回應格式是較好的做法。</span><span class="sxs-lookup"><span data-stu-id="48a2e-122">However, it is good practice explicitly specify the response format.</span></span>  
  
 <span data-ttu-id="48a2e-123">其他作業會使用 `WebInvokeAttribute` 屬性，並且明確地指定回應型別為 JSON 而不是 XML。</span><span class="sxs-lookup"><span data-stu-id="48a2e-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 <span data-ttu-id="48a2e-124">請注意，在這兩種情況中，作業都會傳回屬於標準 `MathResult` 資料合約型別的複雜型別 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="48a2e-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] data contract type.</span></span>  
  
 <span data-ttu-id="48a2e-125">用戶端網頁 XmlAjaxClientPage.htm 包含的 JavaScript 程式碼叫用前述兩項作業的其中一個當使用者按一下**執行計算 (傳回 JSON)** 或**執行計算 (傳回 XML)** 網頁上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="48a2e-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="48a2e-126">叫用此服務的程式碼會建構 JSON 本文，然後使用 HTTP POST 加以傳送。</span><span class="sxs-lookup"><span data-stu-id="48a2e-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="48a2e-127">建立要求以手動方式在 JavaScript 中，不同於[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例，並使用 ASP.NET AJAX 的其他範例。</span><span class="sxs-lookup"><span data-stu-id="48a2e-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>  

```csharp
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```

 <span data-ttu-id="48a2e-128">當服務回應時，回應會不經任何處理地顯示在頁面的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="48a2e-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="48a2e-129">這麼做是為了示範，以便您可直接觀察所使用的 XML 和 JSON 資料格式。</span><span class="sxs-lookup"><span data-stu-id="48a2e-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  <span data-ttu-id="48a2e-130">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="48a2e-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="48a2e-131">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="48a2e-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="48a2e-132">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="48a2e-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48a2e-133">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="48a2e-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="48a2e-134">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="48a2e-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="48a2e-135">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="48a2e-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="48a2e-136">中所述，建置此方案 XmlAjaxService.sln[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="48a2e-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="48a2e-137">瀏覽至http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm（不要在瀏覽器從專案目錄開啟 XmlAjaxClientPage.htm）。</span><span class="sxs-lookup"><span data-stu-id="48a2e-137">Navigate to http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a2e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48a2e-138">See Also</span></span>  
 [<span data-ttu-id="48a2e-139">使用 HTTP POST 的 AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="48a2e-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
