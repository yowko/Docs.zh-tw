---
title: 基本 AJAX 服務
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 7a9529b79c9993e045e6bb28a7ad608f453a694e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509983"
---
# <a name="basic-ajax-service"></a><span data-ttu-id="11427-102">基本 AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="11427-102">Basic AJAX Service</span></span>
<span data-ttu-id="11427-103">此範例示範如何使用 Windows Communication Foundation (WCF) 來建立基本 ASP.NET Asynchronous JavaScript 與 XML (AJAX) 服務 （您可以使用 Web 瀏覽器用戶端的 JavaScript 程式碼存取的服務）。</span><span class="sxs-lookup"><span data-stu-id="11427-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="11427-104">此服務會使用 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性來確保服務回應 HTTP GET 要求，並且設定為以 JavaScript Object Notation (JSON) 資料格式做為回應的格式。</span><span class="sxs-lookup"><span data-stu-id="11427-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>  
  
 <span data-ttu-id="11427-105">在 WCF 中的 AJAX 支援最適合用於透過 ASP.NET AJAX`ScriptManager`控制項。</span><span class="sxs-lookup"><span data-stu-id="11427-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="11427-106">使用 WCF 與 ASP.NET AJAX 的範例，請參閱[AJAX 範例](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)。</span><span class="sxs-lookup"><span data-stu-id="11427-106">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11427-107">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="11427-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="11427-108">在下列程式碼中，<xref:System.ServiceModel.Web.WebGetAttribute> 屬性會套用至 `Add` 作業以確定服務會回應 HTTP GET 要求。</span><span class="sxs-lookup"><span data-stu-id="11427-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="11427-109">為了簡單起見，此段程式碼會使用 GET (您可以從任何 Web 瀏覽器建構 HTTP GET 要求)。</span><span class="sxs-lookup"><span data-stu-id="11427-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="11427-110">您也可以使用 GET 啟用快取。</span><span class="sxs-lookup"><span data-stu-id="11427-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="11427-111">若是缺少 `WebGetAttribute` 屬性，HTTP POST 便會是預設值。</span><span class="sxs-lookup"><span data-stu-id="11427-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 <span data-ttu-id="11427-112">此範例 .svc 檔案會使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>，以便將 <xref:System.ServiceModel.Description.WebScriptEndpoint> 標準端點加入至服務。</span><span class="sxs-lookup"><span data-stu-id="11427-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="11427-113">此端點是在與 .svc 檔相對的空白位址上設定。</span><span class="sxs-lookup"><span data-stu-id="11427-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="11427-114">這表示服務的位址是`http://localhost/ServiceModelSamples/service.svc`，使用作業名稱以外的任何其他後置字元。</span><span class="sxs-lookup"><span data-stu-id="11427-114">This means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <span data-ttu-id="11427-115"><xref:System.ServiceModel.Description.WebScriptEndpoint> 已預先設定，可讓您從 ASP.NET AJAX 用戶端頁面存取服務。</span><span class="sxs-lookup"><span data-stu-id="11427-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="11427-116">Web.config 中的以下區段可用來針對端點進行其他組態變更。</span><span class="sxs-lookup"><span data-stu-id="11427-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="11427-117">如果不需要額外的變更，也可以加以移除。</span><span class="sxs-lookup"><span data-stu-id="11427-117">It can be removed if no extra changes are required.</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name=""  />  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="11427-118"><xref:System.ServiceModel.Description.WebScriptEndpoint> 會將服務的預設資料格式設定為 JSON 而不是 XML。</span><span class="sxs-lookup"><span data-stu-id="11427-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="11427-119">若要叫用服務，請巡覽至`http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200`之後完成註冊的集合，並建置本主題稍後所示的步驟。</span><span class="sxs-lookup"><span data-stu-id="11427-119">To invoke the service, navigate to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="11427-120">這個測試功能會在使用 HTTP GET 要求時啟用。</span><span class="sxs-lookup"><span data-stu-id="11427-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>  
  
 <span data-ttu-id="11427-121">用戶端網頁 SimpleAjaxClientPage.aspx 包含 ASP.NET 程式碼，此程式碼會在使用者每次按下網頁上其中一個作業按鈕時叫用此服務。</span><span class="sxs-lookup"><span data-stu-id="11427-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="11427-122">`ScriptManager` 控制項會用來設定可透過 JavaScript 存取之服務的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="11427-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 <span data-ttu-id="11427-123">這時會具現化 (Instantiated) 本機 Proxy，並使用下列 JavaScript 程式碼叫用作業。</span><span class="sxs-lookup"><span data-stu-id="11427-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 <span data-ttu-id="11427-124">如果此服務呼叫成功，該段程式碼就會叫用 `onSuccess` 處理常式，而作業結果會顯示於文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="11427-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  <span data-ttu-id="11427-125">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="11427-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="11427-126">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="11427-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="11427-127">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="11427-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="11427-128">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="11427-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="11427-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11427-129">See also</span></span>
