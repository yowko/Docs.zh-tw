---
title: WCF Web HTTP 格式化
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: 884193dc26794be5e8a3c95e05be2ca43a90f6e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643484"
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="7be46-102">WCF Web HTTP 格式化</span><span class="sxs-lookup"><span data-stu-id="7be46-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="7be46-103">WCF Web HTTP 程式設計模型可讓您動態決定服務作業傳回回應所使用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="7be46-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="7be46-104">兩種可用來判斷最適合格式的方法分別為：自動和明確。</span><span class="sxs-lookup"><span data-stu-id="7be46-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="7be46-105">自動格式化</span><span class="sxs-lookup"><span data-stu-id="7be46-105">Automatic formatting</span></span>  
 <span data-ttu-id="7be46-106">啟用時，自動格式化會選擇傳回回應所使用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="7be46-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="7be46-107">此方法會透過依序檢查下列各項來判斷最佳格式：</span><span class="sxs-lookup"><span data-stu-id="7be46-107">It determines the best format by checking the following, in order:</span></span>  
  
1. <span data-ttu-id="7be46-108">要求訊息之 Accept 標頭中的媒體類型。</span><span class="sxs-lookup"><span data-stu-id="7be46-108">The media types in the request message’s Accept header.</span></span>  
  
2. <span data-ttu-id="7be46-109">要求訊息的內容類型。</span><span class="sxs-lookup"><span data-stu-id="7be46-109">The content-type of the request message.</span></span>  
  
3. <span data-ttu-id="7be46-110">作業中的預設格式設定。</span><span class="sxs-lookup"><span data-stu-id="7be46-110">The default format setting in the operation.</span></span>  
  
4. <span data-ttu-id="7be46-111">WebHttpBehavior 中的預設格式設定。</span><span class="sxs-lookup"><span data-stu-id="7be46-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="7be46-112">如果要求訊息包含 Accept 標頭的 Windows Communication Foundation (WCF) 基礎結構會搜尋它支援的類型。</span><span class="sxs-lookup"><span data-stu-id="7be46-112">If the request message contains an Accept header the Windows Communication Foundation (WCF) infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="7be46-113">如果 `Accept` 標頭指定其媒體類型的優先權，則會遵循優先權。</span><span class="sxs-lookup"><span data-stu-id="7be46-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="7be46-114">如果 `Accept` 標頭中找不到適合的格式，則會使用要求訊息的內容類型。</span><span class="sxs-lookup"><span data-stu-id="7be46-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="7be46-115">如果未指定適合的內容類型，則會使用作業的預設格式設定。</span><span class="sxs-lookup"><span data-stu-id="7be46-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="7be46-116">預設格式會使用 `ResponseFormat` 和 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性的 <xref:System.ServiceModel.Web.WebInvokeAttribute> 參數設定。</span><span class="sxs-lookup"><span data-stu-id="7be46-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="7be46-117">如果作業上未指定預設格式，則會使用 <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="7be46-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="7be46-118">自動格式化會仰賴 <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7be46-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="7be46-119">當此屬性設定為 `true` 時，WCF 基礎結構會判斷要使用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="7be46-119">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="7be46-120">為了提供回溯相容性，自動格式選取預設為停用。</span><span class="sxs-lookup"><span data-stu-id="7be46-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="7be46-121">自動格式選取可以透過程式設計方式或透過組態啟用。</span><span class="sxs-lookup"><span data-stu-id="7be46-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="7be46-122">下列範例顯示如何在程式碼中啟用自動格式選取。</span><span class="sxs-lookup"><span data-stu-id="7be46-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
```csharp
// This code assumes the service name is MyService and the service contract is IMyContract     
Uri baseAddress = new Uri("http://localhost:8000");  
  
WebServiceHost host = new WebServiceHost(typeof(MyService), baseAddress)  
try  
{  
   ServiceEndpoint sep = host.AddServiceEndpoint(typeof(IMyContract), new WebHttpBinding(), "");  
   // Check it see if the WebHttpBehavior already exists  
   WebHttpBehavior whb = sep.Behaviors.Find<WebHttpBehavior>();  
  
   if (whb != null)  
   {  
      whb.AutomaticFormatSelectionEnabled = true;  
   }  
   else  
   {  
      WebHttpBehavior webBehavior = new WebHttpBehavior();  
      webBehavior.AutomaticFormatSelectionEnabled = true;  
      sep.Behaviors.Add(webBehavior);  
   }  
         // Open host to start listening for messages  
   host.Open();        
  
  // ...  
}  
  catch(CommunicationException ex)  
  {  
     Console.WriteLine("An exception occurred: " + ex.Message());  
  }  
```  
  
 <span data-ttu-id="7be46-123">自動格式化也可以透過組態啟用。</span><span class="sxs-lookup"><span data-stu-id="7be46-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="7be46-124">您可以直接在 <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> 上設定 <xref:System.ServiceModel.Description.WebHttpBehavior> 屬性，或是使用 <xref:System.ServiceModel.Description.WebHttpEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="7be46-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="7be46-125">下列範例示範如何在 <xref:System.ServiceModel.Description.WebHttpBehavior> 上啟用自動格式選取。</span><span class="sxs-lookup"><span data-stu-id="7be46-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <endpointBehaviors>  
      <behavior>  
        <webHttp automaticFormatSelectionEnabled="true" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
      <standardEndpoint name="" helpEnabled="true" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="7be46-126">下列範例顯示如何使用 <xref:System.ServiceModel.Description.WebHttpEndpoint> 啟用自動格式選取。</span><span class="sxs-lookup"><span data-stu-id="7be46-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
        <standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true"  />  
      </webHttpEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```  
  
## <a name="explicit-formatting"></a><span data-ttu-id="7be46-127">明確格式化</span><span class="sxs-lookup"><span data-stu-id="7be46-127">Explicit formatting</span></span>  
 <span data-ttu-id="7be46-128">明確格式化如其名稱所指，可讓開發人員決定要在作業程式碼內使用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="7be46-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="7be46-129">如果最佳格式為 XML 或 JSON，則開發人員會將 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> 設定為 <xref:System.ServiceModel.Web.WebMessageFormat.Xml> 或 <xref:System.ServiceModel.Web.WebMessageFormat.Json>。</span><span class="sxs-lookup"><span data-stu-id="7be46-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="7be46-130">如果未明確設定 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> 屬性，則會使用作業的預設格式。</span><span class="sxs-lookup"><span data-stu-id="7be46-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="7be46-131">下列範例會檢查格式查詢字串參數，找出要使用的格式。</span><span class="sxs-lookup"><span data-stu-id="7be46-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="7be46-132">如果已指定，則該參數會使用 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> 設定作業的格式。</span><span class="sxs-lookup"><span data-stu-id="7be46-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
```csharp
public class Service : IService  
{  
    [WebGet]  
     public string EchoWithGet(string s)  
    {  
        // if a format query string parameter has been specified, set the response format to that. If no such
        // query string parameter exists the Accept header will be used
        string formatQueryStringValue = WebOperationContext.Current.IncomingRequest.UriTemplateMatch.QueryParameters["format"];  
        if (!string.IsNullOrEmpty(formatQueryStringValue))  
        {  
            if (formatQueryStringValue.Equals("xml", System.StringComparison.OrdinalIgnoreCase))  
            {
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Xml;
            }
            else if (formatQueryStringValue.Equals("json", System.StringComparison.OrdinalIgnoreCase))  
            {  
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Json;  
            }  
            else  
            {  
                throw new WebFaultException<string>($"Unsupported format '{formatQueryStringValue}'",   HttpStatusCode.BadRequest);
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 <span data-ttu-id="7be46-133">如果您需要支援 XML 或 JSON 以外的格式，請定義讓作業使用傳回型別 <xref:System.ServiceModel.Channels.Message>。</span><span class="sxs-lookup"><span data-stu-id="7be46-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="7be46-134">請在作業程式碼內決定要使用的適當格式，然後使用下列其中一個方法建立 <xref:System.ServiceModel.Channels.Message> 物件：</span><span class="sxs-lookup"><span data-stu-id="7be46-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="7be46-135">每個方法都會以適當的格式取得內容並且建立訊息。</span><span class="sxs-lookup"><span data-stu-id="7be46-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="7be46-136">`WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` 方法可用來取得用戶端慣用的格式清單，並依照由高到低的順序排列偏好設定。</span><span class="sxs-lookup"><span data-stu-id="7be46-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="7be46-137">下列程式碼顯示如何使用 `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` 決定要使用的格式，然後使用適當的建立回應方法建立回應訊息。</span><span class="sxs-lookup"><span data-stu-id="7be46-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
```csharp
public class Service : IService  
{  
    public Message EchoListWithGet(string list)  
    {  
        List<string> returnList = new List<string>(list.Split(new char[] { ',' }, StringSplitOptions.RemoveEmptyEntries));  
        IList<ContentType> acceptHeaderElements = WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements();  
        for (int x = 0; x < acceptHeaderElements.Count; x++)  
        {  
            string normalizedMediaType = acceptHeaderElements[x].MediaType.ToLowerInvariant();  
            switch (normalizedMediaType)  
            {  
                case "image/jpeg": return CreateJpegResponse(returnList);  
                case "application/xhtml+xml": return CreateXhtmlResponse(returnList);  
                case "application/atom+xml": return CreateAtom10Response(returnList);  
                case "application/xml": return CreateXmlResponse(returnList);  
                case "application/json": return CreateJsonResponse(returnList);  
          }  
    }  
  
    // Default response format is XML  
    return CreateXmlResponse(returnList);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7be46-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7be46-138">See also</span></span>

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [<span data-ttu-id="7be46-139">WCF Web HTTP 程式設計模型</span><span class="sxs-lookup"><span data-stu-id="7be46-139">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="7be46-140">UriTemplate 與 UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="7be46-140">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="7be46-141">WCF Web HTTP 程式設計模型概觀</span><span class="sxs-lookup"><span data-stu-id="7be46-141">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="7be46-142">WCF Web HTTP 程式設計物件模型</span><span class="sxs-lookup"><span data-stu-id="7be46-142">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
