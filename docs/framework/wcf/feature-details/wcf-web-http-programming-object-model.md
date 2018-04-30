---
title: WCF Web HTTP 程式設計物件模型
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
caps.latest.revision: 40
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7bf6512be6fabb87797fb6338f64320d5787d547
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-web-http-programming-object-model"></a>WCF Web HTTP 程式設計物件模型
WCF WEB HTTP 程式設計模型可讓開發人員透過基本 HTTP 要求即可公開 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web 服務，而不需要使用 SOAP。 WCF WEB HTTP 程式設計模型建置在現有 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 擴充性模型之上。 這個模型會定義下列類別：  
  
 **程式設計模型：**  
  
-   <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute>  
  
-   <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
-   <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **通道與發送器基礎結構：**  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
-   <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **公用程式類別和擴充性點：**  
  
-   <xref:System.UriTemplate>  
  
-   <xref:System.UriTemplateTable>  
  
-   <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
-   <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>，套用至服務作業時，表示組態檔中的 ASP.NET 輸出快取設定檔，此設定檔應該用來快取 ASP .NET 輸出快取中作業傳來的回應。 此屬性僅採用一個參數，也就是在組態檔中指定快取設定的快取設定檔名稱。  
  
## <a name="webgetattribute"></a>WebGetAttribute  
 您可以使用 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性將服務作業標示為回應至 HTTP GET 要求。 這是一種被動作業行為 (<xref:System.ServiceModel.Description.IOperationBehavior> 方法不會執行任何動作)，會將中繼資料新增至作業描述中。 套用 <xref:System.ServiceModel.Web.WebGetAttribute> 會沒有作用，除非已將在作業描述 (尤其是 <xref:System.ServiceModel.Description.WebHttpBehavior>) 中尋找此中繼資料的行為新增至服務的行為集合中。 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性會採用下表所示的選用參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`BodyStyle`|控制是否要將屬性所套用至的服務作業中，所傳送和接收的要求和回應包裝起來。|  
|`RequestFormat`|控制格式化要求訊息的方法。|  
|`ResponseFormat`|控制格式化回應訊息的方法。|  
|`UriTemplate`|指定 URI 樣板，這個樣板會控制對應至套用屬性之服務作業的 HTTP 要求。|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 <xref:System.ServiceModel.WebHttpBinding> 類別透過使用 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>，併入了 XML、JSON 和原始二進位資料的支援。 這是由 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>、<xref:System.ServiceModel.Channels.HttpTransportBindingElement> 和 <xref:System.ServiceModel.WebHttpSecurity> 物件所組成。 <xref:System.ServiceModel.WebHttpBinding> 是設計與 <xref:System.ServiceModel.Description.WebHttpBehavior> 配合使用。  
  
## <a name="webinvokeattribute"></a>WebInvokeAttribute  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性類似於 <xref:System.ServiceModel.Web.WebGetAttribute>，但它可用來將服務作業標示為回應至 GET 以外的 HTTP 要求。 這是一種被動作業行為 (<xref:System.ServiceModel.Description.IOperationBehavior> 方法不會執行任何動作)，會將中繼資料新增至作業描述中。 套用 <xref:System.ServiceModel.Web.WebInvokeAttribute> 會沒有作用，除非已將在作業描述 (尤其是 <xref:System.ServiceModel.Description.WebHttpBehavior>) 中尋找此中繼資料的行為新增至服務的行為集合中。  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性會採用下表所示的選用參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`BodyStyle`|控制是否要將屬性所套用至的服務作業中，所傳送和接收的要求和回應包裝起來。|  
|`Method`|指定服務作業對應至的 HTTP 方法。|  
|`RequestFormat`|控制格式化要求訊息的方法。|  
|`ResponseFormat`|控制格式化回應訊息的方法。|  
|`UriTemplate`|指定 URI 樣板，這個樣板會控制對應至套用屬性之服務作業的 GET 要求。|  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> 類別可讓您定義一組結構類似的 URI。 樣板中則包含兩個部分：路徑和查詢。 路徑則包含一系列以斜線 (/) 分隔的區段。 每個區段都有常值、 變數值 （寫在大括號 [{}]，限制為符合一個區段的內容） 或使用萬用字元 (以星號 [\*]，它會比對"其餘的部分路徑 」)，它必須出現在在路徑結尾。 可以完全省略查詢運算式。 如果出現，會指定一系列非循序的名稱/值組。 查詢運算式的項目可以是常值組 (？ x = 2) 或變數組 (？ x = {*值*})。 不允許使用未成對的值。 <xref:System.UriTemplate> WEB HTTP 程式設計模型會在內部使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，以將特定 URI 或 URI 群組對應至服務作業。  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> 類別表示一組相關聯的 <xref:System.UriTemplate> 物件，而這限制為開發人員所選擇的物件。 它可讓您比對候選的統一資源識別元 (URI) 和該組物件中的範本，並擷取與相符範本關聯的資料。 <xref:System.UriTemplateTable> WEB HTTP 程式設計模型會在內部使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，以將特定 URI 或 URI 群組對應至服務作業。  
  
## <a name="webservicehost"></a>WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost> 會擴充 <xref:System.ServiceModel.ServiceHost>，讓它可更輕鬆裝載非 SOAP Web 式服務。 如果 <xref:System.ServiceModel.Web.WebServiceHost> 在服務描述中找不到端點，則會自動在服務的基底位址中建立預設端點。 建立預設 HTTP 端點時，<xref:System.ServiceModel.Web.WebServiceHost> 也會停用 HTTP 說明網頁和 Web 服務描述語言 (WSDL) 的 GET 功能，使中繼資料端點不會干擾預設 HTTP 端點。 <xref:System.ServiceModel.Web.WebServiceHost> 也會確保所有使用 <xref:System.ServiceModel.WebHttpBinding> 的端點都已附加必要的 <xref:System.ServiceModel.Description.WebHttpBehavior>。 最後，<xref:System.ServiceModel.Web.WebServiceHost> 會自動設定端點的繫結，以在安全虛擬目錄中使用時處理相關聯的網際網路資訊服務 (IIS) 安全性設定。  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 當服務是在網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 下裝載時，可以使用 <xref:System.ServiceModel.Activation.WebServiceHostFactory> 類別以動態建立 <xref:System.ServiceModel.Web.WebServiceHost>。 和主應用程式在其中具現化 <xref:System.ServiceModel.Web.WebServiceHost> 的自我裝載服務不同，透過 IIS 或 WAS 裝載的服務會使用這個類別來建立用於服務的 <xref:System.ServiceModel.Web.WebServiceHost>。 接收到服務的傳入要求時，就會呼叫 <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> 方法。  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> 類別會對服務模型層中的 Web 式服務支援，提供必要的格式器、作業選取器等等。 這個動作會實作為端點行為 (用於與 <xref:System.ServiceModel.WebHttpBinding> 搭配使用)，並可對每個端點指定格式器和作業選取器，因此可讓相同的服務實作可同時公開 SOAP 和 POX 端點。  
  
### <a name="extending-webhttpbehavior"></a>擴充 WebHttpBehavior  
 使用一些虛擬方法即可擴充 <xref:System.ServiceModel.Description.WebHttpBehavior>：<xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>、<xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>、<xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>、<xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29> 和 <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>。 開發人員可以從 <xref:System.ServiceModel.Description.WebHttpBehavior> 衍生類別，並覆寫這些方法以自訂預設行為。  
  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> 是擴充 <xref:System.ServiceModel.Description.WebHttpBehavior> 的範例。 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> 讓 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 端點可從瀏覽器型 ASP.NET AJAX 用戶端接收 HTTP 要求。 [AJAX 服務使用 HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)是使用此擴充性點的範例。  
  
> [!WARNING]
>  當使用 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> 時，<xref:System.UriTemplate> 或 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性內不支援<xref:System.ServiceModel.Web.WebInvokeAttribute>。  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> 類別會使用 <xref:System.UriTemplate> 和 <xref:System.UriTemplateTable> 類別，以將呼叫分派至服務作業。  
  
## <a name="compatibility"></a>相容性  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP 程式設計模型不會使用 SOAP 型訊息，因此不會支援 WS-* 通訊協定。 不過，您可以透過兩個不同的端點來公開相同的合約：一個端點使用 SOAP，而另一個端點不使用 SOAP。 請參閱[如何： 公開給 SOAP 和 Web 用戶端合約](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md)的範例。  
  
## <a name="security"></a>安全性  
 由於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP 程式設計模型不支援 WS-* 通訊協定，要保護 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP 程式設計模型上所建置 Web 服務安全的唯一方法，即是運用 SSL 公開服務。 如需有關設定 SSL 使用[!INCLUDE[iisver](../../../../includes/iisver-md.md)]看到[如何在 IIS 中實作 SSL](http://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
 [WCF Web HTTP 程式設計模型概觀](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
