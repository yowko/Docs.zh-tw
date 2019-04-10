---
title: WCF Web HTTP 格式化
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: f3d3a2d992f234c690f3fb87514b700a6596a5fe
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331035"
---
# <a name="wcf-web-http-formatting"></a>WCF Web HTTP 格式化
WCF Web HTTP 程式設計模型可讓您動態決定服務作業傳回回應所使用的最佳格式。 兩種可用來判斷最適合格式的方法分別為：自動和明確。  
  
## <a name="automatic-formatting"></a>自動格式化  
 啟用時，自動格式化會選擇傳回回應所使用的最佳格式。 此方法會透過依序檢查下列各項來判斷最佳格式：  
  
1. 要求訊息之 Accept 標頭中的媒體類型。  
  
2. 要求訊息的內容類型。  
  
3. 作業中的預設格式設定。  
  
4. WebHttpBehavior 中的預設格式設定。  
  
 如果要求訊息包含 Accept 標頭的 Windows Communication Foundation (WCF) 基礎結構會搜尋它支援的類型。 如果 `Accept` 標頭指定其媒體類型的優先權，則會遵循優先權。 如果 `Accept` 標頭中找不到適合的格式，則會使用要求訊息的內容類型。 如果未指定適合的內容類型，則會使用作業的預設格式設定。 預設格式會使用 `ResponseFormat` 和 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性的 <xref:System.ServiceModel.Web.WebInvokeAttribute> 參數設定。 如果作業上未指定預設格式，則會使用 <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> 屬性的值。 自動格式化會仰賴 <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> 屬性。 當此屬性設定為 `true` 時，WCF 基礎結構會判斷要使用的最佳格式。 為了提供回溯相容性，自動格式選取預設為停用。 自動格式選取可以透過程式設計方式或透過組態啟用。 下列範例顯示如何在程式碼中啟用自動格式選取。  
  
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
  
 自動格式化也可以透過組態啟用。 您可以直接在 <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> 上設定 <xref:System.ServiceModel.Description.WebHttpBehavior> 屬性，或是使用 <xref:System.ServiceModel.Description.WebHttpEndpoint>。 下列範例示範如何在 <xref:System.ServiceModel.Description.WebHttpBehavior> 上啟用自動格式選取。  
  
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
  
 下列範例顯示如何使用 <xref:System.ServiceModel.Description.WebHttpEndpoint> 啟用自動格式選取。  
  
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
  
## <a name="explicit-formatting"></a>明確格式化  
 明確格式化如其名稱所指，可讓開發人員決定要在作業程式碼內使用的最佳格式。 如果最佳格式為 XML 或 JSON，則開發人員會將 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> 設定為 <xref:System.ServiceModel.Web.WebMessageFormat.Xml> 或 <xref:System.ServiceModel.Web.WebMessageFormat.Json>。 如果未明確設定 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> 屬性，則會使用作業的預設格式。  
  
 下列範例會檢查格式查詢字串參數，找出要使用的格式。 如果已指定，則該參數會使用 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> 設定作業的格式。  
  
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
  
 如果您需要支援 XML 或 JSON 以外的格式，請定義讓作業使用傳回型別 <xref:System.ServiceModel.Channels.Message>。 請在作業程式碼內決定要使用的適當格式，然後使用下列其中一個方法建立 <xref:System.ServiceModel.Channels.Message> 物件：  
  
-   `WebOperationContext.CreateAtom10Response`  
  
-   `WebOperationContext.CreateJsonResponse`  
  
-   `WebOperationContext.CreateStreamResponse`  
  
-   `WebOperationContext.CreateTextResponse`  
  
-   `WebOperationContext.CreateXmlResponse`  
  
 每個方法都會以適當的格式取得內容並且建立訊息。 `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` 方法可用來取得用戶端慣用的格式清單，並依照由高到低的順序排列偏好設定。 下列程式碼顯示如何使用 `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` 決定要使用的格式，然後使用適當的建立回應方法建立回應訊息。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [UriTemplate 與 UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [WCF Web HTTP 程式設計模型概觀](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [WCF Web HTTP 程式設計物件模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
